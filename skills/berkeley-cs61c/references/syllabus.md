# CS 61C Syllabus

## Course Information

- **Course**: CS 61C — Great Ideas in Computer Architecture (Machine Structures)
- **University**: UC Berkeley
- **Term**: Spring 2026
- **Prerequisites**: CS 61A (Introduction to Computer Science), CS 61B (Data Structures)
- **Website**: https://cs61c.org/sp26/

## Unit Breakdown

### Unit 1: Introduction & C Programming (Weeks 1–3)

- Course intro and logistics
- Number representation: binary, hex, two's complement
- IEEE 754 floating-point representation
- C programming fundamentals
- Types, operators, control flow
- Pointers and memory addresses
- Arrays and pointer arithmetic
- The C memory model (stack, heap, data, text)
- Compilation model: preprocessor → compiler → assembler → linker
- Debugging with GDB

### Unit 2: Digital Logic (Weeks 3–5)

- Boolean algebra
- Logic gates: AND, OR, NOT, NAND, NOR, XOR
- Combinational logic circuits
- Multiplexers, decoders, encoders
- Adders and ALUs
- Sequential logic
- Flip-flops and registers
- Finite state machines (FSMs)
- Clock and timing
- Introduction to Verilog / logisim

### Unit 3: RISC-V Assembly (Weeks 5–8)

- RISC-V philosophy and history
- RV32I base integer instruction set
- Register file: x0–x31
- Arithmetic instructions: ADD, SUB, AND, OR, XOR, SLL, SRL, SRA
- Immediate instructions: ADDI, ANDI, ORI, XORI, SLLI, SRLI, SRAI
- Load/Word: LW, SW, LH, LB, SH, SB
- Branch instructions: BEQ, BNE, BLT, BGE, BLTU, BGEU
- Jump instructions: JAL, JALR
- Pseudo-instructions (LI, LA, MV, NOP, J, BGT, etc.)
- Addressing modes
- The calling convention
- Stack frames and the stack pointer
- Leaf vs non-leaf functions
- Translating C to assembly and back

### Unit 4: Processor Design (Weeks 8–11)

- The instruction execution cycle: Fetch → Decode → Execute → Memory → Writeback
- Single-cycle datapath
- Control unit design
- Performance metrics: CPI, clock cycle, throughput
- Motivation for pipelining
- The 5-stage pipeline: IF, ID, EX, MEM, WB
- Pipelined datapath and control
- Structural hazards
- Data hazards: RAW, WAW, WAR
- Hazard detection unit
- Forwarding (bypassing)
- Load-use hazard
- Control hazards
- Branch prediction: always taken, 1-bit, 2-bit saturating counter
- Branch target buffer
- Exceptions and interrupts

### Unit 5: Memory Hierarchy & Caches (Weeks 11–13)

- The memory wall
- Principles of locality
  - Temporal locality
  - Spatial locality
- Cache basics: tags, index, offset
- Cache performance: hit rate, miss rate, miss penalty
- Three C's of cache misses: Compulsory, Capacity, Conflict
- Direct-mapped caches
- Set-associative caches
- Fully associative caches
- Replacement policies: LRU, FIFO, random
- Write policies: write-through, write-back
- Write allocation vs no-write allocation
- Multi-level caches (L1, L2, L3)
- Cache optimization techniques
- Prefetching

### Unit 6: Parallelism (Weeks 13–15)

- Types of parallelism
- Instruction-level parallelism (ILP)
- Loop unrolling
- VLIW and superscalar architectures
- Thread-level parallelism (TLP)
- Amdahl's Law
- Flynn's taxonomy
- Shared-memory vs distributed-memory multiprocessors
- Coherence problem
- Snooping protocols
- Directory-based protocols
- Synchronization: locks, semaphores, barriers
- Race conditions and atomicity
- SIMD (Single Instruction, Multiple Data)
- Vector processors and GPU basics

### Unit 7: Virtual Memory (Weeks 15–16)

- Motivation for virtual memory
- Virtual vs physical addresses
- Address spaces
- Page tables
- Page table entry format
- TLB (Translation Lookaside Buffer)
- TLB hit, TLB miss, page fault
- Multi-level page tables
- Inverted page tables
- Page replacement algorithms
- Protection and access permissions
- Memory-mapped files
- Copy-on-write
- Thrashing

## Lab Projects

CS 61C typically includes 4–6 hands-on labs:

1. **Lab 1**: C programming and number representation
2. **Lab 2**: C pointers, memory, and debugging
3. **Lab 3**: RISC-V assembly programming
4. **Lab 4**: Processor design (single-cycle or pipelined)
5. **Lab 5**: Cache simulation or implementation
6. **Lab 6**: Parallel programming (OpenMP, pthreads, or SIMD)

## Grading (Typical)

| Component       | Weight |
|----------------|--------|
| Midterm         | 20%    |
| Final           | 30%    |
| Labs            | 30%    |
| Homework        | 15%    |
| Participation   | 5%     |

## Textbook

**Computer Organization and Design: The Hardware/Software Interface** (RISC-V Edition)
- Authors: David A. Patterson, John L. Hennessy
- Publisher: Morgan Kaufmann
- ISBN: 978-0128201091

## Additional References

- *The C Programming Language* — Kernighan & Ritchie
- *Computer Systems: A Programmer's Perspective* — Bryant & O'Hallaron
- *Digital Design and Computer Architecture* — Harris & Harris
