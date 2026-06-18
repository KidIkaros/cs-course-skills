# CS 61C Key Concepts

## The Great Ideas

CS 61C is organized around eight great ideas in computer architecture:

1. **Abstraction** — Hide details behind a clean interface (ISA, OS, compiler)
2. **Moore's Law** — Transistor density doubles approximately every 18–24 months
3. **Principle of Locality** — Programs reuse data and instructions near those recently used
4. **Parallelism** — Do multiple things simultaneously for performance
5. **Performance Measurement & Improvement** — Measure, model, and optimize
6. **Dependability via Redundancy** — Build reliable systems with redundant components
7. **Caching** — Keep copies of frequently used data in faster memory
8. **Virtualization** — Create an illusion of more resources than physically exist

---

## Number Representation

### Integer Encoding

- **Unsigned binary**: Straightforward base-2 representation
- **Two's complement**: Negate by inverting bits and adding 1
  - Range for n bits: −2^(n−1) to 2^(n−1) − 1
  - MSB is the sign bit
- **Overflow**: When result exceeds representable range
  - Signed overflow: adding two positives gives negative (or vice versa)
  - Unsigned overflow: wraps around modulo 2^n

### Floating Point (IEEE 754)

- **Single precision (32-bit)**: 1 sign bit, 8 exponent bits, 23 mantissa bits
- **Double precision (64-bit)**: 1 sign bit, 11 exponent bits, 52 mantissa bits
- **Excess/Bias representation**: Exponent stored as unsigned + bias (127 for single, 1023 for double)
- **Special values**: ±0, ±∞, NaN, denormals
- **Normalization**: 1.xxxx × 2^exp (hidden leading 1)

---

## C Programming

### Memory Model

```
+------------------+ High address
|     Environment  |
+------------------+
|       Stack      | ← grows downward (local vars, return addresses)
+------------------+
|        ↓         |
|                  |
|        ↑         |
+------------------+
|       Heap       | ← grows upward (malloc, calloc, realloc)
+------------------+
|   BSS (uninit)   |
+------------------+
| Data (initialized)|
+------------------+
|      Text        | ← program code (read-only)
+------------------+ Low address
```

### Pointers

- A pointer stores a memory address
- `*p` dereferences — gives value at address
- `&x` takes address of variable
- Pointer arithmetic: `p + n` adds `n * sizeof(*p)` bytes
- Arrays decay to pointers: `arr` ≡ `&arr[0]`

### Common Pitfalls

- Dangling pointers (using freed memory)
- Memory leaks (malloc without free)
- Buffer overflows (writing past array bounds)
- Null pointer dereference
- Use-after-free
- Uninitialized variables

---

## RISC-V Assembly

### Register Convention

| Register | ABI Name | Usage |
|----------|----------|-------|
| x0 | zero | Hardwired to 0 |
| x1 | ra | Return address |
| x2 | sp | Stack pointer |
| x3 | gp | Global pointer |
| x4 | tp | Thread pointer |
| x5–x7 | t0–t2 | Temporaries |
| x8 | s0/fp | Saved / frame pointer |
| x9 | s1 | Saved register |
| x10–x11 | a0–a1 | Function args / return values |
| x12–x17 | a2–a7 | Function arguments |
| x18–x27 | s2–s11 | Saved registers |
| x28–x31 | t3–t6 | Temporaries |

### Instruction Formats

- **R-type**: opcode | rd | funct3 | rs1 | rs2 | funct7
- **I-type**: opcode | rd | funct3 | rs1 | imm[11:0]
- **S-type**: opcode | imm[4:0] | funct3 | rs1 | rs2 | imm[11:5]
- **B-type**: opcode | imm[12|10:5] | funct3 | rs1 | rs2 | imm[4:1|11]
- **U-type**: opcode | rd | imm[31:12]
- **J-type**: opcode | rd | imm[20|10:1|11|19:12]

### Calling Convention

1. Caller saves: t0–t6, a0–a7
2. Callee saves: s0–s11
3. Arguments in a0–a7 (stack for >8 args)
4. Return value in a0 (a1 for 64-bit on 32-bit)
5. Stack must be 8-byte aligned (16-byte for some ABIs)

---

## Processor Design

### Single-Cycle Datapath

```
Instruction Memory → Register File → ALU → Data Memory → Write Back
     ↑                    ↑                              ↓
     +--- PC (updated) ---+------------------------------+
```

- All instructions complete in one clock cycle
- Clock period determined by longest instruction (load)
- Simple but slow

### 5-Stage Pipeline

| Stage | Name | What Happens |
|-------|------|-------------|
| IF | Instruction Fetch | Read instruction from memory at PC |
| ID | Instruction Decode | Decode instruction, read registers |
| EX | Execute | ALU operation, compute address, branch comparison |
| MEM | Memory Access | Load from or store to data memory |
| WB | Write Back | Write result back to register file |

### Hazards

**Data Hazards (RAW — Read After Write)**
- Instruction depends on result of previous instruction still in pipeline
- Solutions: stalling, forwarding/bypassing

**Load-Use Hazard**
- Load result needed by very next instruction
- Must stall one cycle even with forwarding

**Control Hazards**
- Branch outcome not known until MEM or WB stage
- Solutions: branch prediction, delayed branch, early branch resolution

### Forwarding Paths

```
EX/MEM pipeline register → ALU input (EX stage)
MEM/WB pipeline register → ALU input (EX stage)
```

### Branch Prediction

- **Static**: Always predict taken or not taken
- **1-bit**: Single prediction bit, mispredicts in loops
- **2-bit saturating counter**: Requires two mispredictions to change prediction
- **Correlating predictors**: Use history of recent branches
- **Tournament predictors**: Combine multiple prediction schemes

---

## Memory Hierarchy & Caches

### Locality

- **Temporal locality**: If you accessed an item recently, you'll likely access it again soon
- **Spatial locality**: If you accessed an item, you'll likely access nearby items soon

### Cache Organization

```
Address = [ Tag | Index | Offset ]
```

- **Offset**: Selects byte within cache line (log2(block size) bits)
- **Index**: Selects cache set (log2(number of sets) bits)
- **Tag**: Identifies which memory block is stored (remaining bits)

### Cache Types

| Type | Description | Pros | Cons |
|------|-------------|------|------|
| Direct-mapped | Each block maps to exactly one cache line | Simple, fast | High conflict misses |
| Set-associative | Each block maps to one set with n ways | Balance | More complex, slower lookup |
| Fully associative | Any block can go anywhere | Fewest conflicts | Expensive search |

### Replacement Policies

- **LRU (Least Recently Used)**: Evict the block used longest ago
- **FIFO**: Evict the oldest block
- **Random**: Evict a random block

### Write Policies

- **Write-through**: Write to cache and memory simultaneously
  - Simple, but slow (writes to memory every time)
- **Write-back**: Write only to cache; write to memory when evicted
  - Faster, but more complex (dirty bits needed)

### Three C's of Misses

1. **Compulsory (cold)**: First access to a block — unavoidable
2. **Capacity**: Cache too small to hold all needed blocks
3. **Conflict**: Multiple blocks compete for same cache slot (direct-mapped)

### Cache Performance

- **AMAT (Average Memory Access Time)** = Hit Time + Miss Rate × Miss Penalty
- Multi-level caches: AMAT = L1 Hit Time + L1 Miss Rate × (L2 Hit Time + L2 Miss Rate × Memory Access Time)

---

## Parallelism

### Amdahl's Law

```
Speedup = 1 / ((1 - f) + f/s)

f = fraction of code that is parallelizable
s = speedup factor for parallel portion
```

- Even with infinite parallelism, speedup is bounded by serial portion
- 50% parallel code → max 2× speedup
- 90% parallel code → max 10× speedup

### Flynn's Taxonomy

| Type | Description |
|------|-------------|
| SISD | Single Instruction, Single Data |
| SIMD | Single Instruction, Multiple Data |
| MISD | Multiple Instruction, Single Data |
| MIMD | Multiple Instruction, Multiple Data |

### Coherence

- **Coherence problem**: Multiple caches may hold copies of the same memory location
- **Coherence property**: Any read returns the value of the most recent write
- **Snooping protocols**: Broadcast invalidations on shared bus
- **MSI**: Modified, Shared, Invalid states
- **MESI**: Adds Exclusive state

### Consistency

- **Sequential consistency**: Operations appear in some sequential order consistent with program order
- **Relaxed models**: Allow reordering for performance (requires explicit fences/barriers)

---

## Virtual Memory

### Address Translation

```
Virtual Address = [ VPN | Page Offset ]
Physical Address = [ PPN | Page Offset ]
```

- VPN → PPN translation stored in page table
- Page offset unchanged during translation

### TLB (Translation Lookaside Buffer)

- Cache for page table entries
- Speeds up address translation
- TLB hit: Use cached translation (1 cycle)
- TLB miss: Walk page table (many cycles)
- Page fault: Page not in physical memory (OS handles)

### Page Table Structure

- **Single-level**: Simple but large for large address spaces
- **Multi-level (hierarchical)**: Only allocate tables for used regions
- **Inverted**: One entry per physical page, search by VPN

### Page Replacement

- **FIFO**: Replace oldest page
- **LRU**: Replace least recently used page
- **Clock (Second Chance)**: Approximation of LRU
- **Optimal**: Replace page not used for longest time (theoretical, not implementable)

### Protection

- Each page table entry has permission bits: Read, Write, Execute
- User/supervisor mode bits
- Access violations trigger exceptions (segfault)

---

## Performance

### Metrics

- **CPU Time** = Instruction Count × CPI × Clock Cycle Time
- **CPI** (Cycles Per Instruction) = Clock Cycles / Instructions
- **MIPS** = Instructions / (Time × 10^6)
- **MFLOPS** = Floating-point operations / (Time × 10^6)

### Speedup

```
Speedup = Performance_old / Performance_new
        = Execution_time_old / Execution_time_new
```

### Roofline Model

- Peak performance = min(Peak FLOPS, Bandwidth × Operational Intensity)
- Operational Intensity = FLOPs / Bytes accessed
