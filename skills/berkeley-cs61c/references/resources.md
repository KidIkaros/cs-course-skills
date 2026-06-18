# CS 61C Resources

## Course Materials

- **Course Website**: https://cs61c.org/sp26/
- **Lecture Recordings**: Available on the course website
- **Ed Discussion**: Course forum (check website for link)
- **Gradescope**: For homework and lab submissions

## Textbook

### Primary Text
- **Computer Organization and Design: The Hardware/Software Interface** (RISC-V Edition)
  - Authors: David A. Patterson, John L. Hennessy
  - Publisher: Morgan Kaufmann
  - ISBN: 978-0128201091
  - Supplementary materials: https://www.elsevier.com/books/computer-organization-and-design/patterson/978-0-12-820109-1

### Supplementary Texts
- **The C Programming Language** (K&R) — Brian W. Kernighan, Dennis M. Ritchie
  - THE reference for C. Compact and authoritative.
- **Computer Systems: A Programmer's Perspective** — Randal E. Bryant, David R. O'Hallaron
  - Deeper dive into systems from a programmer's perspective
- **Digital Design and Computer Architecture** — David Money Harris, Sarah L. Harris
  - Great for the digital logic portions
- **The Elements of Computing Systems** (Nand2Tetris) — Noam Nisan, Shimon Schocken
  - Builds a computer from first principles

## Online Resources

### RISC-V
- **RISC-V Specifications**: https://riscv.org/technical/specifications/
- **RISC-V ISA Simulator (RARS)**: https://github.com/TheThirdOne/rars
  - Java-based RISC-V simulator for running assembly
- **Venus**: https://venus.cs61c.org/
  - Browser-based RISC-V simulator (CS 61C specific)
- **RISC-V Green Card**: Reference card for RV32I instructions
- **RISC-V Instruction Set Cheat Sheet**: https://www.cs.cornell.edu/courses/cs3410/2019sp/riscv/interpreter/

### C Programming
- **The GNU C Library Manual**: https://www.gnu.org/software/libc/
- **GDB Documentation**: https://sourceware.org/gdb/documentation/
- **GDB Quick Reference**: https://darkdust.net/files/GDB%20Cheat%20Sheet.pdf
- **cdecl**: http://cdecl.org/ — Decipher C declarations
- **Compiler Explorer (Godbolt)**: https://godbolt.org/ — See assembly output for C code

### Digital Logic
- **Logisim Evolution**: https://github.com/logisim-evolution/logisim-evolution
  - Digital logic simulator used in labs
- **Digital Logic Simulator**: https://www.nand2tetris.org/course
- **Boolean Algebra Cheat Sheet**: https://www.electronics-tutorials.ws/boolean/boolean.html

### Pipelining & Processor Design
- **MIPS Pipeline Simulator**: http://www.cs.umd.edu/class/fall2019/cmsc411/projects.html
- **Virgo**: Berkeley's processor visualization tool (check course website)
- **Patterson & Hennessy Lecture Slides**: Available via textbook publisher

### Caches & Memory
- **Cache Lab Guide**: Available on course website
- **Memory Hierarchy Tutorial**: https://www.cs.cornell.edu/courses/cs3410/2022sp/

### Parallelism
- **OpenMP Reference**: https://www.openmp.org/specifications/
- **POSIX Threads Tutorial**: https://beej.us/guide/bgnet/

### Virtual Memory
- **Virtual Memory Paper**: (check course readings)
- **OS/161**: Teaching OS used at some universities
- **xv6**: Teaching OS from MIT — great for understanding VM: https://pdos.csail.mit.edu/6.828/2023/xv6.html

## Development Tools

### Compilers & Toolchains
```bash
# GCC (standard)
gcc -Wall -Wextra -g -o program program.c

# Cross-compiler for RISC-V (if not on course VM)
riscv64-unknown-elf-gcc
riscv32-unknown-elf-gcc

# Clang (alternative)
clang -Wall -Wextra -g -o program program.c
```

### Debuggers
```bash
# GDB basics
gdb ./program
(gdb) break main
(gdb) run
(gdb) step        # step into
(gdb) next        # step over
(gdb) continue
(gdb) print var
(gdb) backtrace
(gdb) info registers
(gdb) layout asm  # assembly view
(gdb) layout src  # source view
```

### Simulators
- **RARS** (RISC-V): Java-based, supports syscalls
- **Venus** (web): Browser-based, no installation
- **Logisim Evolution**: For digital logic labs
- **MARS**: MIPS simulator (for reference/comparison)

## Practice & Study

### Problem Sets
- CS 61C past exams and homework (check course website)
- Patterson & Hennessy textbook exercises
- Nand2Tetris projects (complementary)

### Video Lectures
- **Berkeley CS 61C Lectures**: https://www.youtube.com/results?search_query=berkeley+cs+61c
- **O'Reilly: Computer Architecture**: Various online courses
- **Ben Eater YouTube**: Excellent digital logic and computer architecture videos
  - https://www.youtube.com/c/beneater
- **Nand2Tetris Coursera**: https://www.coursera.org/learn/nand2tetris1

### Interactive Learning
- **Nand2Tetris**: Build a computer from logic gates to OS
- **Little Man Computer**: Simplified computer architecture for learning
- **CPU Simulator**: Various online tools for building CPUs

## Supplementary Courses

- **MIT 6.004**: Computation Structures — similar content, different approach
- **Stanford CS 107**: Computer Organization & Systems
- **CMU 15-213**: Introduction to Computer Systems (CSAPP)
- **Cornell CS 3410**: Computer System Organization and Programming

## Quick Reference

### RISC-V RV32I Instructions

| Instruction | Format | Operation |
|-------------|--------|-----------|
| ADD rd, rs1, rs2 | R | rd = rs1 + rs2 |
| SUB rd, rs1, rs2 | R | rd = rs1 - rs2 |
| AND rd, rs1, rs2 | R | rd = rs1 & rs2 |
| OR rd, rs1, rs2 | R | rd = rs1 \| rs2 |
| XOR rd, rs1, rs2 | R | rd = rs1 ^ rs2 |
| SLL rd, rs1, rs2 | R | rd = rs1 << rs2 |
| SRL rd, rs1, rs2 | R | rd = rs1 >> rs2 (logical) |
| SRA rd, rs1, rs2 | R | rd = rs1 >> rs2 (arithmetic) |
| ADDI rd, rs1, imm | I | rd = rs1 + imm |
| LW rd, imm(rs1) | I | rd = Mem[rs1 + imm] |
| SW rs2, imm(rs1) | S | Mem[rs1 + imm] = rs2 |
| BEQ rs1, rs2, imm | B | if (rs1 == rs2) PC += imm |
| BNE rs1, rs2, imm | B | if (rs1 != rs2) PC += imm |
| JAL rd, imm | J | rd = PC + 4; PC += imm |
| JALR rd, rs1, imm | I | rd = PC + 4; PC = rs1 + imm |

### IEEE 754 Single Precision

```
Sign (1 bit) | Exponent (8 bits) | Mantissa (23 bits)
     S        |    E (bias=127)   |      M
```

- Value = (-1)^S × 1.M × 2^(E-127)
- Exponent 0: denormalized (implicit leading 0)
- Exponent 255: infinity or NaN

### Cache Formulas

```
AMAT = Hit Time + Miss Rate × Miss Penalty
Block Offset bits = log2(Block Size)
Index bits = log2(Cache Size / (Block Size × Associativity))
Tag bits = Address bits - Index bits - Block Offset bits
```
