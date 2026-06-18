# Compiler Concepts Cheat Sheet

Quick reference for core concepts from CS 6120.

---

## Intermediate Representations (IRs)

### SSA Form (Static Single Assignment)
- Every variable is assigned exactly once
- Phi-nodes merge values at control-flow join points
- Enables simple and efficient optimizations
- Construct via: dominance, frontier computation, phi insertion, renaming

### Dominance
- A **dominates** B if every path from entry to B passes through A
- **Immediate dominator** (idom): the closest strict dominator
- **Dominance frontier**: the set of nodes where a node's dominance ends

### Control Flow Graph (CFG)
- Nodes: basic blocks (straight-line code)
- Edges: control flow between blocks
- Entry block (no predecessors), exit block (no successors)
- Back edges indicate loops

---

## Data Flow Analysis

### Liveness Analysis (Backward)
- Variable is **live** at point P if its value may be read before next definition
- Live-in, live-out sets per block
- Transfer: `live-in = use union (live-out - def)`
- Join: union

### Reaching Definitions (Forward)
- Definition **reaches** point P if there is a path from def to P without redefinition
- Gen/Kill per block
- Transfer: `out = gen union (in - kill)`
- Join: union

### Worklist Algorithm
1. Initialize all blocks
2. Add all blocks to worklist
3. While worklist not empty:
   - Pop block B
   - Compute new in/out sets
   - If changed, add successors to worklist
4. Repeat until fixpoint

### Monotone Framework
- Transfer functions must be monotone (preserves order)
- Meet operator must be idempotent, commutative, associative
- Guarantees convergence in finite iterations

---

## SSA-Based Optimizations

### Global Value Numbering (GVN)
- Assign each unique computed value a number
- Two expressions get same number if they compute the same value
- Detects redundant computations

### Partial Redundancy Elimination (PRE)
- Eliminates computations that are redundant on some paths
- May insert computations on non-redundant paths to make all paths redundant
- Combines strength reduction and redundancy elimination

### Sparse Conditional Constant Propagation (SCCP)
- Merges constant propagation with unreachable code elimination
- Uses a lattice: Top, then constants, then Bottom
- Only processes edges that are actually executable
- Eliminates dead branches when condition is constant

---

## Loop Optimizations

### Loop-Invariant Code Motion (LICM)
1. Identify loop-invariant instructions (all inputs defined outside loop or invariant)
2. Check for dependencies (must not reorder with other invariant instructions)
3. Hoist to loop preheader (create if needed)
4. Handle exceptions (may need to guard hoisted instructions)

### Loop Unrolling
- Replicate loop body N times, adjust trip count
- Reduces branch overhead, exposes ILP
- Trade-off: code size vs. performance
- Perfect unrolling: trip count known at compile time

### Loop Tiling
- Break loop nest into tiles that fit in cache
- Improves data locality
- Example: matrix multiply tiled for L1 cache

### Polyhedral Model
- Represent loop bounds and accesses as integer polyhedra
- Affine transformations: permutation, skewing, tiling
- Automatic parallelism and locality optimization

---

## Register Allocation

### Graph Coloring Approach
1. Build **interference graph**: nodes = variables, edges = simultaneous live ranges
2. **K-color** the graph (k = number of physical registers)
3. If not k-colorable, **spill** some variables to memory
4. Assign physical registers based on colors

### Spilling
- Move variable to stack when not enough registers
- Re-load into register when needed
- Choose spill candidates by cost (use frequency times cost)

---

## Memory Management

### Allocation Strategies
- **Bump allocation**: advance pointer; fastest but no deallocation
- **Free list**: maintain list of free blocks; O(1) amortized
- **Region-based**: allocate into regions; free entire region at once
- **Generational**: separate by age; collect young objects frequently

### Escape Analysis
- Determine if object escapes its creating scope
- If no escape: can allocate on stack or in region
- Enables stack allocation, dead allocation elimination

---

## Garbage Collection

### Mark-and-Sweep
1. **Mark**: trace from roots, mark reachable objects
2. **Sweep**: scan heap, free unmarked objects
- Non-copying; causes fragmentation
- Pause time proportional to heap size

### Copying Collector
- Copy live objects from from-space to to-space
- Compact in process (no fragmentation)
- Cheney's algorithm: BFS using a queue

### Generational GC
- Young generation (nursery): small, collected frequently
- Old generation: large, collected infrequently
- Write barrier: track old-young references for minor GC

### Concurrent GC
- Run collection concurrently with mutator
- Reduce pause times
- Requires synchronization (read/write barriers)

---

## Parallelism

### Vectorization (DLP)
- Transform scalar operations to SIMD
- Loop vectorization: process multiple iterations simultaneously
- Requires aligned data, no loop-carried dependencies

### Thread-Level Parallelism
- Fork-join parallelism
- Work scheduling: static vs dynamic
- Synchronization: locks, barriers, atomics

### Polyhedral Parallelism
- Extract parallelism from loop nests via affine transformations
- Software pipelining, loop skewing, tiling

---

## Instruction Selection and Scheduling

### Tree Pattern Matching
- Represent operations as trees
- Match machine instruction patterns to tree nodes
- Tools: burg, twig

### Instruction Scheduling
- Reorder instructions to fill pipeline slots
- Respect dependencies (data, control, anti)
- List scheduling: greedy priority-based ordering

---

## JIT Compilation

### Tracing JIT
- Record hot execution paths (traces)
- Optimize traces independently
- Handle side exits and guard checks

### Method-at-a-Time JIT
- Compile entire methods on first call
- Use profile data for optimization decisions
- Tiered: interpreter, baseline compiler, optimizing compiler

### Speculation
- Optimistically compile with assumptions
- Insert guards to check assumptions
- Deoptimize and recompile if assumptions violated
