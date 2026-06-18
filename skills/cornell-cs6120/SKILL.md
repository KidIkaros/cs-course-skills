---
name: "cornell-cs6120"
description: "Cornell CS 6120 - Advanced Compilers. Use when learning compiler implementation, intermediate representations, data flow analysis, SSA, LLVM, optimizations, memory management, JIT compilation, and parallelism. Self-guided PhD-level course."
metadata:
  university: "Cornell University"
  level: "advanced"
  topics: ["compilers", "LLVM", "SSA", "data flow", "optimization", "JIT", "garbage collection"]
  url: "https://www.cs.cornell.edu/courses/cs6120/2025fa/self-guided/"
---

# Cornell CS 6120 - Advanced Compilers

**Instructor:** Adrian Sampson
**University:** Cornell University
**Format:** Free self-guided OpenCourseWare (videos + papers + implementation tasks)
**URL:** https://www.cs.cornell.edu/courses/cs6120/2025fa/self-guided/

## When to Use

- Learning compiler infrastructure and IR design
- Understanding data flow analysis and optimization theory
- Implementing optimizations in LLVM or Bril
- Studying SSA form, loop optimizations, and memory management
- Building JIT compilers or garbage collectors
- Preparing for compiler engineering interviews or research

## Course Overview

CS 6120 covers advanced compiler topics beyond introductory courses. The curriculum is organized around 14 self-paced lessons, each with lecture videos, assigned papers, and implementation tasks. The course uses two main tools: **Bril** (an educational IR from Cornell) and **LLVM** (production compiler infrastructure).

## 14 Lessons

| # | Lesson | Topics |
|---|--------|--------|
| 1 | Introduction & Course Overview | What compilers do, course logistics, the optimization pipeline |
| 2 | Intermediary Representations | SSA, SSA construction, Bril, LLVM IR |
| 3 | Data Flow Analysis | Iterative data flow, worklist algorithms, liveness, reaching definitions |
| 4 | Dead Code Elimination & Constant Propagation | Peephole optimizations, SCCP, DCE |
| 5 | Loop Optimizations | LICM, unrolling, tiling, polyhedral model |
| 6 | SSA-Based Optimizations | GVN, PRE, phi-node elimination, memory SSA |
| 7 | Instruction Selection & Scheduling | Tree patterns, register allocation, instruction scheduling |
| 8 | Abstraction & Lowering | High-level vs low-level IRs, representation tradeoffs |
| 9 | Optimization by Dynamic Profiling | Basic block profiling, edge profiling, Dynamo, hot/cold paths |
| 10 | Memory Management | Heap allocation, region-based allocation, escape analysis |
| 11 | Garbage Collection | Mark-and-sweep, copying collectors, generational GC, concurrent GC |
| 12 | Parallelism & Vectorization | Auto-vectorization, polyhedral optimization, SIMD, multithreading |
| 13 | LLVM in Practice | LLVM passes, writing custom passes, debugging LLVM |
| 14 | JIT Compilation | Tracing JITs, method-at-a-time JITs, tiered compilation, runtime optimization |

## Implementation Tools

### Bril (Educational IR)
- **Language:** TypeScript
- **Install:** `npm install -g bril-ts` or clone from https://github.com/sampsyo/bril
- **Features:** SSA-form IR, simple syntax, good for implementing analysis passes
- **Use cases:** Data flow analysis, optimization passes, teaching IR concepts

### LLVM (Production Infrastructure)
- **Language:** C++ (with C bindings)
- **Install:** https://llvm.org/docs/GettingStarted.html
- **Features:** Mature pass infrastructure, extensive optimizations, multiple frontends
- **Use cases:** Learning real compiler infrastructure, implementing production-quality passes

## Key Research Papers

Each lesson includes assigned papers. The core papers across the course include:

- **SSA:** Cytron et al. "Efficiently Computing Static Single Assignment Form"
- **Data Flow:** Kildall "A Simple Approach to Global Program Optimizations"
- **LICM:** Morel & Renvoise "Global Optimization by Suppression of Partial Redundancies"
- **Register Allocation:** Chaitin "Register Allocation & Spilling via Graph Coloring"
- **Garbage Collection:** Wilson "Uniprocessor Garbage Collection Techniques"
- **Polyhedral:** Bondhugula et al. "A Practical Automatic Polyhedral Parallelizer"
- **Tracing JIT:** Bezman et al. "Optimizing Indirect Branches in Dynamic Binary Translators"

## Recommended Study Order

1. Start with lessons 1-3 (IR, SSA, data flow) — foundational
2. Complete lessons 4-6 (optimizations) — core techniques
3. Study lessons 7-8 (lowering, instruction selection) — backend
4. Cover lessons 9-11 (profiling, memory, GC) — runtime
5. Finish with lessons 12-14 (parallelism, LLVM, JIT) — advanced

## How to Use This Skill

Ask about:
- "Explain SSA construction" — get theory and Bril implementation guidance
- "Implement constant propagation" — walkthrough with code examples
- "How does LLVM pass infrastructure work?" — practical LLVM guidance
- "Write a garbage collector" — theory and implementation in Bril
- "Optimize this loop" — LICM, unrolling, vectorization strategies
- "Data flow analysis for this IR" — worklist algorithm walkthrough

## Prerequisites

- Familiarity with at least one systems programming language (C, C++, Rust)
- Basic understanding of compilation (lexing, parsing, code generation)
- Familiarity with graph theory (for register allocation, SSA, data flow)
- Comfortable reading academic papers

## References

See `references/` directory for detailed content:
- `syllabus.md` — Full lesson breakdown with videos and papers
- `key-concepts.md` — Compiler concepts cheat sheet
- `exercises.md` — Implementation tasks using Bril and LLVM
- `resources.md` — Papers, LLVM documentation, tools

## See Also

- `cornell-cs4820` - Cornell CS 4820 - Introduction to Analysis of Algorithms
- `mit-6006` - MIT 6.006 - Introduction to Algorithms
