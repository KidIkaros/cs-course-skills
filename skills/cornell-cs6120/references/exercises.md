# CS 6120 Implementation Exercises

Practical tasks using Bril and LLVM. Each exercise corresponds to a course lesson.

---

## Lesson 2: SSA Construction

**Goal:** Implement SSA construction for Bril programs.

**Steps:**
1. Parse a Bril JSON program into a CFG
2. Compute dominators using the iterative algorithm
3. Compute dominance frontiers
4. Insert phi-nodes at dominance frontiers
5. Rename variables using a stack-based approach

**Bril JSON structure:**
```json
{
  "functions": [
    {
      "name": "main",
      "instrs": [
        {"op": "const", "dest": "x", "type": "int", "value": 1},
        {"op": "add", "dest": "y", "type": "int", "args": ["x", "x"]}
      ]
    }
  ]
}
```

**Hints:**
- Use `successors` field on branch/jump instructions to build CFG edges
- Dominance frontier of node n: nodes m where n dominates a predecessor of m but n does not strictly dominate m
- For renaming: maintain a stack per variable name; push on define, pop at scope exit

---

## Lesson 3: Data Flow Analysis Framework

**Goal:** Build a generic worklist-based data flow analysis framework.

**Interface:**
```typescript
interface Analysis {
  init(): Map<Block, Set<string>>;
  transfer(block: Block, input: Set<string>): Set<string>;
  meet(a: Set<string>, b: Set<string>): Set<string>;
}
```

**Implement:**
1. Liveness analysis (backward, union meet)
2. Reaching definitions (forward, union meet)
3. Available expressions (forward, intersection meet)

**Test cases:**
- Linear chains
- Diamond-shaped CFGs
- Loops with back edges

---

## Lesson 4: Sparse Conditional Constant Propagation

**Goal:** Implement SCCP in Bril.

**Lattice:**
- Top (T) = unknown/uninitialized
- Constant(v) = known constant value v
- Bottom (B) = not a constant (overdefined)

**Algorithm:**
1. Initialize all variables to Top
2. Maintain executable edges set
3. For each executable block:
   - Update variable values based on operations
   - For conditional branches: if condition is constant, add only taken edge
4. When value changes, add successors to worklist
5. Remove dead branches and replace constant uses

**Test cases:**
```bril
// Constant propagation
@main(x: int) -> int {
  a: int = const 5;
  b: int = add a x;
  ret b;
}
// If x=3, should produce 8
```

---

## Lesson 5: Loop-Invariant Code Motion

**Goal:** Implement LICM in Bril.

**Steps:**
1. Identify loops (find back edges in DFS)
2. Build loop membership set
3. Find loop-invariant instructions:
   - All operands are defined outside the loop, OR
   - All operands are themselves loop-invariant
4. Check safety:
   - No other instructions in the loop depend on this one
   - Destination is not live at any loop exit
5. Create preheader block if needed
6. Move invariant instructions to preheader

**Test case:**
```bril
@main(n: int) -> int {
  i: int = const 0;
  sum: int = const 0;
  config: int = const 42;  // loop-invariant
loop:
  cond: bool = lt i n;
  br cond body done;
body:
  x: int = mul i config;  // can hoist (config is invariant)
  sum2: int = add sum x;
  i2: int = add i const 1;
  jmp loop;
done:
  ret sum;
}
```

---

## Lesson 6: Global Value Numbering

**Goal:** Implement GVN for Bril.

**Algorithm:**
1. Visit blocks in dominator tree order
2. For each instruction:
   - Compute value number for each argument
   - Look up (op, value_numbers) in a hash table
   - If found: replace with existing value
   - If not found: assign new value number, add to table
3. Handle phi-nodes separately (value number based on control flow)

**Test case:**
```bril
@main(x: int) -> int {
  a: int = add x x;
  b: int = add x x;   // redundant with a
  c: int = mul a b;   // uses a and b (same value)
  ret c;
}
// After GVN: b should be replaced with a
```

---

## Lesson 7: Register Allocation

**Goal:** Implement graph-coloring register allocation.

**Steps:**
1. Run liveness analysis to get live ranges
2. Build interference graph:
   - Two variables interfere if their live ranges overlap
   - Add edges between interfering variables
3. Select K (number of physical registers, e.g., 4)
4. Simplify: remove node with degree < K, push to stack
5. Select: pop from stack, assign color not used by neighbors
6. If unable to select: spill to memory

**Helper functions needed:**
- `buildInterferenceGraph(liveness)`
- `simplify(graph, K)`
- `select(graph, K)`
- `spill(graph, K)`

---

## Lesson 9: Edge Profiling

**Goal:** Instrument Bril programs to count edge executions.

**Approach:**
1. For each CFG edge, add an instrumented counter
2. At each branch, increment counter for taken edge
3. At function end, output counter values

**Implementation:**
```typescript
function instrument(program: BrilProgram): BrilProgram {
  // For each function:
  // 1. Add counter variables for each edge
  // 2. Before each branch, add increment instructions
  // 3. At exit, print counter values
}
```

**Analysis:**
- Compute edge frequencies from counter values
- Identify hot loops (high trip counts)
- Calculate branch probabilities

---

## Lesson 10: Region-Based Memory Management

**Goal:** Implement region allocation in Bril.

**Concepts:**
- Each region has a bump pointer and a size limit
- Allocation increments the pointer
- When region is full, allocate new region
- Freeing a region reclaims all its memory

**Implementation:**
1. Add `region.new`, `region.alloc`, `region.free` operations
2. In Bril, model regions as arrays with a bump pointer
3. Track active regions on a stack
4. On `region.free`, reset bump pointer to start

---

## Lesson 11: Mark-and-Sweep Garbage Collector

**Goal:** Implement a mark-and-sweep GC in Bril.

**Data structures:**
- Heap: array of objects, each with a mark bit and fields
- Root set: stack of local variables and globals
- Free list: linked list of unmarked objects

**Algorithm:**
1. **Mark phase:** BFS/DFS from roots, set mark bit on reachable objects
2. **Sweep phase:** scan heap, add unmarked objects to free list, clear marks

**Bril-specific:**
- Model heap as a global array
- Objects are indices into the array
- Each object has a mark bit (0 or 1) and field values

---

## Lesson 12: Simple Auto-Vectorizer

**Goal:** Detect and vectorize SIMD-friendly loops in Bril.

**Detection criteria:**
- Loop has no loop-carried dependencies (except induction variable)
- Operations are element-wise (add, mul, etc.)
- Trip count is known or can be computed

**Transformation:**
1. Identify vectorizable operations
2. Replace scalar operations with vector-width operations
3. Adjust loop trip count (divide by vector width)
4. Handle remainder loop for non-multiple trip counts

**Test case:**
```bril
@main(n: int, a: int[], b: int[], c: int[]) {
  i: int = const 0;
loop:
  cond: bool = lt i n;
  br cond body done;
body:
  ai: int = load a i;
  bi: int = load b i;
  ci: int = add ai bi;
  store c i ci;
  i2: int = add i const 1;
  jmp loop;
done:
  ret;
}
// Vectorizable: a[i] + b[i] -> c[i]
```

---

## Lesson 13: Custom LLVM Pass

**Goal:** Write an LLVM pass that performs constant folding.

**Steps:**
1. Create an LLVM FunctionPass
2. Iterate over instructions in each basic block
3. For binary operations where both operands are constants:
   - Compute the result
   - Replace all uses with the constant result
   - Mark the instruction for deletion
4. Clean up dead instructions

**Skeleton:**
```cpp
#include "llvm/IR/Function.h"
#include "llvm/Pass.h"

struct ConstantFolderPass : public FunctionPass {
  static char ID;
  ConstantFolderPass() : FunctionPass(ID) {}

  bool runOnFunction(Function &F) override {
    bool changed = false;
    for (auto &BB : F) {
      for (auto II = BB.begin(); II != BB.end(); ) {
        auto &I = *II++;
        if (auto *BO = dyn_cast<BinaryOperator>(&I)) {
          auto *LHS = dyn_cast<ConstantInt>(BO->getOperand(0));
          auto *RHS = dyn_cast<ConstantInt>(BO->getOperand(1));
          if (LHS && RHS) {
            Constant *Result = ConstantFoldBinaryOp(BO, LHS, RHS);
            BO->replaceAllUsesWith(Result);
            BO->eraseFromParent();
            changed = true;
          }
        }
      }
    }
    return changed;
  }
};
```

---

## Lesson 14: Tracing JIT

**Goal:** Implement a simple tracing JIT for Bril.

**Components:**
1. **Trace recorder:** Monitor hot loops, record instruction sequence
2. **Trace compiler:** Optimize recorded trace (constant folding, dead code elimination)
3. **Code emitter:** Replace original loop with compiled trace
4. **Guard insertion:** Add guards for assumptions made during compilation

**Algorithm:**
1. Interpret program until a loop back edge is hit N times
2. Start recording: capture all instructions in the loop body
3. On loop exit, stop recording
4. Optimize the recorded trace
5. Replace original loop with call to compiled trace
6. Add guard at loop entry: if assumptions violated, fall back to interpreter
