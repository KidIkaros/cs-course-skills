# CS 6120 Resources

Papers, documentation, tools, and further reading for CS 6120.

---

## Course Materials

- **Course page:** https://www.cs.cornell.edu/courses/cs6120/2025fa/self-guided/
- **Adrian Sampson's site:** https://www.cs.cornell.edu/~asampson/
- **Bril GitHub:** https://github.com/sampsyo/bril

---

## Key Papers

### IR and SSA
1. Cytron et al., "Efficiently Computing Static Single Assignment Form and the Control Dependence Graph" (1991)
2. Click, "Combining Analyses, Combining Optimizations" (1995)
3. Click, "A Simple Graph-Based Intermediate Representation" (1995)

### Data Flow Analysis
4. Kildall, "A Simple Approach to Global Program Optimizations" (1973)
5. Hecht & Ullman, "Analysis of a Simple Code Optimization Procedure" (1972)

### Constant Propagation and DCE
6. Wegman & Zadeck, "Constant Propagation with Conditional Branches" (1991)
7. Knoop, Rething, & Steffen, "Lazy Code Motion" (1992)

### Loop Optimizations
8. Morel & Renvoise, "Global Optimization by Suppression of Partial Redundancies" (1979)
9. Bondhugula et al., "A Practical Automatic Polyhedral Parallelizer and Locality Optimizer" (2008)
10. Allen & Kennedy, "Automatic Loop Interchange" (1984)

### SSA Optimizations
11. Alpern et al., "Detecting Equality of Variables in Programs" (1988)
12. Rosen, Wegman, & Zadeck, "Global Value Numbers and Redundant Computations" (1988)

### Register Allocation
13. Chaitin et al., "Register Allocation via Graph Coloring" (1981)

### Memory Management and GC
14. Wilson et al., "Uniprocessor Garbage Collection Techniques" (1992)
15. Lattner & Adve, "Automatic Pool Allocation for Disjoint Data Structures" (2005)
16. Bacon & Rajan, "Concurrent Cycle Collection in Reference Counted Systems" (2001)

### LLVM
17. Lattner & Adve, "LLVM: A Compilation Framework for Lifelong Program Analysis & Transformation" (2004)

### JIT Compilation
18. Bezman et al., "Optimizing Indirect Branches in Dynamic Binary Translators" (2001)
19. Bala et al., "Dynamo: A Transparent Dynamic Optimization System" (2000)
20. Gal et al., "HotpathVM: An Effective JIT Compiler for Resource-constrained Devices" (2006)

---

## Tools

### Bril
- **Repository:** https://github.com/sampsyo/bril
- **Documentation:** https://github.com/sampsyo/bril/blob/master/README.md
- **Install:** `npm install -g bril-ts`
- **Commands:**
  - `bril2txt` — Convert JSON to text format
  - `brildoc` — Generate documentation
  - `brillvm` — Compile Bril to LLVM IR
  - `brili` — Interpret Bril
- **TypeScript API:** `@bril-ts` package

### LLVM
- **Documentation:** https://llvm.org/docs/
- **Getting Started:** https://llvm.org/docs/GettingStarted.html
- **Tutorial:** https://llvm.org/docs/tutorial/
- **Passes:** https://llvm.org/docs/Passes.html
- **IR Reference:** https://llvm.org/docs/LangRef.html
- **opt tool:** https://llvm.org/docs/CommandGuide/opt.html
- **Clang:** https://clang.llvm.org/

### Other Tools
- **graphviz:** Graph visualization for CFGs — https://graphviz.org/
- **z3:** SMT solver for verification — https://github.com/Z3Prover/z3
- **alive2:** LLVM optimization verification — https://alive2.llvm.org/
- **creduce:** Test case reduction — https://github.com/csmith-project/creduce
- **cvise:** Faster test case reduction — https://github.com/marxin/cvise

---

## Textbooks

1. **Engineering a Compiler** (Cooper & Torczon) — Practical compiler engineering
2. **Advanced Compiler Design and Implementation** (Steven Muchnick) — Comprehensive reference
3. **Modern Compiler Implementation in ML** (Andrew Appel) — Functional approach to compilers
4. **Compilers: Principles, Techniques, and Tools** (Dragon Book) — Classic textbook

---

## Online Resources

- **LLVM Tutorial (Writing an LLVM Pass):** https://llvm.org/docs/WritingAnLLVMPass.html
- **Bril examples:** https://github.com/sampsyo/bril/tree/master/examples
- **CS 6120 blog posts:** Search for "CS 6120" on medium.com for student posts
- **Compiler Explorer (Godbolt):** https://godbolt.org/ — View assembly output
- **Alive2 web:** https://alive2.llvm.org/ce/ — Verify LLVM optimizations

---

## Setup Guides

### Bril Setup
```bash
# Install Node.js (if not installed)
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs

# Install Bril tools
npm install -g bril-ts brili

# Verify installation
bril2txt --help
```

### LLVM Setup
```bash
# Ubuntu/Debian
sudo apt-get install llvm-17 llvm-17-dev llvm-17-tools

# Or build from source
git clone https://github.com/llvm/llvm-project.git
cd llvm-project
mkdir build && cd build
cmake -G Ninja ../llvm -DLLVM_ENABLE_PROJECTS="clang;clang-tools-extra"
ninja
```

---

## Problem Sets Reference

Each lesson has associated implementation tasks. See `exercises.md` for detailed specifications.

| Lesson | Task | Difficulty |
|--------|------|------------|
| 2 | SSA construction | Medium |
| 3 | Data flow framework | Medium |
| 4 | SCCP | Hard |
| 5 | LICM | Medium |
| 6 | GVN | Medium |
| 7 | Register allocation | Hard |
| 9 | Edge profiling | Medium |
| 10 | Region allocation | Medium |
| 11 | Mark-and-sweep GC | Hard |
| 12 | Auto-vectorizer | Hard |
| 13 | LLVM pass | Medium |
| 14 | Tracing JIT | Hard |
