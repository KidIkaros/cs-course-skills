# CS 6120 Syllabus — Lesson Breakdown

**Course:** CS 6120 - Advanced Compilers
**Instructor:** Adrian Sampson
**Semester:** Fall 2025 (self-guided)
**URL:** https://www.cs.cornell.edu/courses/cs6120/2025fa/self-guided/

---

## Lesson 1: Introduction & Course Overview

**Topics:**
- What compilers do and why they matter
- The optimization pipeline: frontend → IR → middle-end → backend → code generation
- Course tools: Bril and LLVM
- Overview of compiler infrastructure

**Video:** [Introduction](https://www.cs.cornell.edu/courses/cs6120/2025fa/self-guided/)

**Key Concepts:**
- Compiler phases: scanning, parsing, semantic analysis, IR generation, optimization, code generation
- The role of intermediate representations
- Why we study optimizations: performance, correctness, portability

**Task:** Set up Bril development environment. Familiarize yourself with the Bril JSON format and `bril2txt`/`brildoc` tools.

---

## Lesson 2: Intermediary Representations

**Topics:**
- Three-address code and SSA form
- SSA construction: dominance, dominance frontiers, phi-nodes
- Bril as an SSA-based IR
- LLVM IR structure and syntax
- Graphical vs. textual IRs

**Papers:**
- Cytron et al., "Efficiently Computing Static Single Assignment Form and the Control Dependence Graph" (1991)
- Click, "Combining Analyses, Combining Optimizations" (1995)

**Key Concepts:**
- **SSA (Static Single Assignment):** Each variable is assigned exactly once; phi-functions merge control flow
- **Dominance:** Node A dominates node B if every path from entry to B goes through A
- **Dominance frontiers:** Where dominance ends — where phi-nodes are needed
- **Pruned SSA:** Only insert phi-nodes for live variables
- **LLVM IR:** Typed SSA, module/function/basic-block hierarchy, SSA registers

**Task:** Implement SSA construction for a Bril program. Given a CFG, compute dominance, insert phi-nodes, and rename variables.

---

## Lesson 3: Data Flow Analysis

**Topics:**
- Iterative data flow analysis framework
- Forward vs. backward analysis
- Meet/join operators, monotone frameworks
- Liveness analysis
- Reaching definitions
- Use-def chains

**Papers:**
- Kildall, "A Simple Approach to Global Program Optimizations" (1973)
- Hecht & Ullman, "Analysis of a Simple Code Optimization Procedure" (1972)

**Key Concepts:**
- **Liveness:** A variable is live at a point if its value may be read before next being defined
- **Reaching definitions:** A definition reaches a point if there is a path from the definition to that point without intervening redefinition
- **Worklist algorithm:** Iterate over blocks until fixpoint; process changed blocks only
- **Monotone framework:** Transfer functions are monotone; meet is idempotent, commutative, associative

**Task:** Implement a worklist-based data flow analysis framework in Bril. Build liveness analysis and reaching definitions on top of it.

---

## Lesson 4: Dead Code Elimination & Constant Propagation

**Topics:**
- Peephole optimizations
- Dead code elimination (DCE)
- Sparse Conditional Constant Propagation (SCCP)
- Folding and simplification

**Papers:**
- Wegman & Zadeck, "Constant Propagation with Conditional Branches" (1991)
- Knoop, Rüthing, & Steffen, "Lazy Code Motion" (1992)

**Key Concepts:**
- **DCE:** Remove instructions whose results are never used
- **SCCP:** Combine constant propagation with unreachable code elimination using a lattice
- **Lattice:** Top (unknown) → constant values → Bottom (not constant)
- **Conditional branches:** SCCP eliminates branches when the condition is provably constant

**Task:** Implement SCCP in Bril. Use a lattice-based approach to propagate constants and eliminate dead branches.

---

## Lesson 5: Loop Optimizations

**Topics:**
- Loop detection and canonical forms
- Loop-Invariant Code Motion (LICM)
- Loop unrolling
- Loop tiling/blocking
- The polyhedral model

**Papers:**
- Morel & Renvoise, "Global Optimization by Suppression of Partial Redundancies" (1979)
- Bondhugula et al., "A Practical Automatic Polyhedral Parallelizer and Locality Optimizer" (2008)

**Key Concepts:**
- **LICM:** Move loop-invariant computations outside the loop body
- **Loop unrolling:** Reduce loop overhead, expose instruction-level parallelism
- **Tiling:** Break loops into cache-friendly blocks
- **Polyhedral model:** Represent loop nests as integer polyhedra; schedule via affine transformations

**Task:** Implement LICM in Bril. Identify loop-invariant instructions and hoist them before the loop header.

---

## Lesson 6: SSA-Based Optimizations

**Topics:**
- Global Value Numbering (GVN)
- Partial Redundancy Elimination (PRE)
- Phi-node elimination
- Memory SSA and alias analysis
- Value numbering in SSA

**Papers:**
- Alpern et al., "Detecting Equality of Variables in Programs" (1988)
- Rosen, Wegman, & Zadeck, "Global Value Numbers and Redundant Computations" (1988)

**Key Concepts:**
- **GVN:** Assign each unique value a number; expressions with same operands get same number
- **PRE:** Eliminate partially redundant computations by inserting copies where needed
- **Memory SSA:** Track memory state as a pseudo-variable in SSA form
- **Alias analysis:** Determine when two pointers may refer to the same memory location

**Task:** Implement GVN on Bril programs. Detect redundant computations using value numbering.

---

## Lesson 7: Instruction Selection & Scheduling

**Topics:**
- Tree pattern matching (burg, twig)
- Instruction selection on DAGs
- Register allocation (graph coloring)
- Instruction scheduling

**Papers:**
- Chaitin et al., "Register Allocation via Graph Coloring" (1981)
- Click, "A Simple Graph-Based Intermediate Representation" (1995)

**Key Concepts:**
- **Instruction selection:** Map IR operations to machine instructions using tree patterns
- **Register allocation:** Assign IR variables to physical registers; spill to stack when necessary
- **Graph coloring:** Build interference graph; k-color to assign registers
- **Instruction scheduling:** Reorder instructions to maximize pipeline utilization

**Task:** Implement a simple register allocator for Bril. Build an interference graph and perform graph coloring.

---

## Lesson 8: Abstraction & Lowering

**Topics:**
- High-level vs. low-level IR design
- Abstraction boundaries in compiler IRs
- Lowering passes (control flow → SSA → machine-level)
- Multi-level IRs

**Papers:**
- Lattner & Adve, "LLVM: A Compilation Framework for Lifelong Program Analysis & Transformation" (2004)

**Key Concepts:**
- **High-level IR:** Preserves source-level semantics, good for high-level optimizations
- **Lowering:** Transform abstract operations into concrete ones (e.g., object allocation → malloc)
- **Multi-level IR:** Use different IR levels for different optimization stages
- **LLVM module/function/basic-block structure**

**Task:** Design a two-level IR in Bril. Implement a lowering pass that transforms high-level constructs (loops, conditionals) into basic blocks.

---

## Lesson 9: Optimization by Dynamic Profiling

**Topics:**
- Basic block profiling
- Edge profiling
- Dynamo and dynamic optimization
- Hot/cold path detection
- Profile-guided optimization (PGO)

**Papers:**
- Bezman et al., "Optimizing Indirect Branches in Dynamic Binary Translators" (2001)
- Bala et al., "Dynamo: A Transparent Dynamic Optimization System" (2000)

**Key Concepts:**
- **Profiling:** Run program to collect runtime statistics (branch frequencies, hot paths)
- **Edge profiling:** Count control-flow edges (more precise than block counts)
- **PGO:** Use profile data to guide optimization decisions
- **Dynamic optimization:** Optimize code at runtime based on observed behavior
- **Hot/cold splitting:** Move cold code out of hot paths to improve instruction cache performance

**Task:** Implement edge profiling in Bril. Add instrumentation to count branch executions and identify hot loops.

---

## Lesson 10: Memory Management

**Topics:**
- Heap allocation strategies (free lists, bump allocation)
- Region-based allocation
- Escape analysis
- Reference counting
- Lifetime analysis

**Papers:**
- Wilson et al., "Uniprocessor Garbage Collection Techniques" (1992)
- Lattner & Adve, "Automatic Pool Allocation for Disjoint Data Structures" (2005)

**Key Concepts:**
- **Bump allocation:** Fast allocation by advancing a pointer; no per-object free list
- **Regions:** Allocate objects into regions; free entire regions at once
- **Escape analysis:** Determine if an object's lifetime exceeds the creating function's scope
- **Reference counting:** Track number of references; free when count reaches zero

**Task:** Implement region-based memory management in Bril. Allocate variables into named regions and free regions at scope exit.

---

## Lesson 11: Garbage Collection

**Topics:**
- Mark-and-sweep collector
- Copying collectors (Cheney's algorithm)
- Generational garbage collection
- Concurrent and incremental GC
- Root sets and tracing

**Papers:**
- Wilson, "Uniprocessor Garbage Collection Techniques" (1992)
- Bacon & Rajan, "Concurrent Cycle Collection in Reference Counted Systems" (2001)

**Key Concepts:**
- **Mark-and-sweep:** Trace from roots, mark reachable objects, sweep unreachable ones
- **Copying collector:** Copy live objects to new space; compact in process
- **Generational GC:** Partition objects by age; collect young generation frequently
- **Concurrent GC:** Run collection concurrently with mutator to reduce pauses

**Task:** Implement a mark-and-sweep garbage collector in Bril. Maintain a root set, trace reachable objects, and free garbage.

---

## Lesson 12: Parallelism & Vectorization

**Topics:**
- Auto-vectorization
- Polyhedral optimization for parallelism
- SIMD (Single Instruction, Multiple Data)
- Multithreading and thread-level parallelism
- Reduction parallelism

**Papers:**
- Bondhugula et al., "A Practical Automatic Polyhedral Parallelizer and Locality Optimizer" (2008)
- Allen & Kennedy, "Automatic Loop Interchange" (1984)

**Key Concepts:**
- **Auto-vectorization:** Transform scalar loops to use SIMD instructions
- **Polyhedral model:** Represent and transform loop nests for parallelism and locality
- **Parallelism levels:** Instruction-level (ILP), thread-level (TLP), data-level (DLP)
- **Reduction:** Summarize values across iterations (e.g., sum, max)

**Task:** Implement a simple auto-vectorizer in Bril. Detect SIMD-friendly loops and emit vector operations.

---

## Lesson 13: LLVM in Practice

**Topics:**
- LLVM pass infrastructure
- Function passes, module passes, loop passes
- Writing custom LLVM passes
- Debugging and analyzing LLVM IR
- LLVM optimization pipeline

**Papers:**
- Lattner & Adve, "LLVM: A Compilation Framework for Lifelong Program Analysis & Transformation" (2004)

**Key Concepts:**
- **Pass infrastructure:** LLVM organizes optimizations as passes that transform IR
- **PassManager:** Schedules passes and manages dependencies
- **Analysis passes:** Provide information consumed by transformation passes
- **Legacy vs new pass manager:** Migration from `PassManager` to `PassBuilder`

**Task:** Write a custom LLVM pass that performs a simple optimization (e.g., constant folding, dead code elimination). Use `opt` to test.

---

## Lesson 14: JIT Compilation

**Topics:**
- Tracing JIT compilers
- Method-at-a-time JITs
- Tiered compilation
- Runtime optimization and speculation
- Just-in-time compilation infrastructure

**Papers:**
- Bezman et al., "Optimizing Indirect Branches in Dynamic Binary Translators" (2001)
- Gal et al., "HotpathVM: An Effective JIT Compiler for Resource-constrained Devices" (2006)

**Key Concepts:**
- **Tracing JIT:** Record and optimize hot execution traces
- **Method JIT:** Compile entire methods/functions at call time
- **Tiered compilation:** Start with fast interpreter, tier up to optimized code
- **Speculation:** Optimistically compile based on assumptions; deoptimize if violated
- **Inline caches:** Optimize dynamic dispatch at call sites

**Task:** Implement a simple tracing JIT in Bril. Record a hot loop, compile it, and replace the original code.
