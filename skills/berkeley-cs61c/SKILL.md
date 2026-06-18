---
name: "berkeley-cs61c"
description: "Berkeley CS 61C - Great Ideas in Computer Architecture. Use when learning C programming, RISC-V assembly, digital logic, processor design, pipelining, caches, parallelism, or virtual memory. Systems fundamentals."
metadata:
  university: "UC Berkeley"
  level: "intermediate"
  topics: ["computer architecture", "C", "RISC-V", "pipelining", "caches", "parallelism"]
  url: "https://cs61c.org/sp26/"
---

# CS 61C — Great Ideas in Computer Architecture (Machine Structures)

## Course Overview

UC Berkeley's CS 61C introduces the fundamental concepts of computer architecture and systems. The course follows the "Great Ideas" framework — abstraction, stored program, local variables, arithmetic operations, time and space complexity, parallelism, locality, and virtualization.

## When to Use This Skill

- Learning C programming from scratch or deepening understanding
- Writing or understanding RISC-V assembly
- Understanding digital logic and processor datapath design
- Learning pipelining, hazard detection, and forwarding
- Studying cache design, locality, and memory hierarchies
- Exploring parallelism (multicore, SIMD, warehouses)
- Understanding virtual memory and address translation

## Course Structure

### Unit 1: Intro & C

- Representation of numbers (two's complement, IEEE 754 floating point)
- C basics: types, pointers, memory layout
- The C compilation model and calling convention
- GDB and debugging tools

### Unit 2: Number Representation & Digital Logic

- Binary, hex, sign extension
- Boolean algebra and logic gates
- Multiplexers, decoders, ALUs
- Combinational vs sequential logic
- FSMs and register design

### Unit 3: RISC-V Assembly

- RV32I base integer instruction set
- Load/store architecture
- Arithmetic, logical, branch instructions
- Functions, calling convention, stack frames
- Translating between C and assembly

### Unit 4: Processor Design

- Single-cycle datapath
- Pipelining (5-stage pipeline)
- Data hazards and hazard detection
- Forwarding (bypassing)
- Control hazards and branch prediction

### Unit 5: Memory Hierarchy & Caches

- Principles of locality (temporal, spatial)
- Direct-mapped caches
- Associative caches (set-associative, fully associative)
- Replacement policies, write policies
- Cache performance and optimization

### Unit 6: Parallelism

- Instruction-level parallelism (ILP)
- Thread-level parallelism (TLP)
- Multiprocessor architectures
- Coherence and synchronization
- SIMD and vector extensions

### Unit 7: Virtual Memory

- Virtual-to-physical address translation
- Page tables and TLBs
- Page faults and demand paging
- Protection and access control
- Memory-mapped files

## Key Commands & Patterns

```bash
# Compile C with debug symbols
gcc -g -o program program.c

# Run in GDB
gdb ./program

# Disassemble a program
objdump -d ./program

# Compile RISC-V assembly (with toolchain)
riscv32-unknown-elf-gcc -o program.s -S program.c
```

## Key Concepts Reference

See `references/key-concepts.md` for the full concepts list.
See `references/exercises.md` for practice problems.
See `references/resources.md` for course links and textbooks.
See `references/syllabus.md` for the complete syllabus.

## Textbook

**Computer Organization and Design: The Hardware/Software Interface** — Patterson & Hennessy (RISC-V Edition)

## Course Format

- Free course website with all materials
- Lecture recordings available
- Lab projects in C, assembly, and Verilog/logisim
- No prerequisites beyond CS 61A and CS 61B

## Notes

- This is a systems-level course — expect to work close to the hardware
- The course uses RISC-V (not MIPS, as in older editions)
- Strong C programming skills are essential for success
- Lab projects are time-intensive — start early
