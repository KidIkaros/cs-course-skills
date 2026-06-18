# CS 61C Practice Exercises

## Unit 1: C Programming & Number Representation

### Exercise 1.1 — Binary Conversion
Convert the following decimal numbers to 8-bit two's complement binary:
- 42
- -17
- 127
- -128

### Exercise 1.2 — Float Representation
What is the IEEE 754 single-precision representation of:
- 6.75
- -0.0
- The smallest positive denormalized number

### Exercise 1.3 — Pointer Tracing
```c
int arr[] = {10, 20, 30, 40, 50};
int *p = arr;
int *q = &arr[3];

printf("%d\n", *p);        // What prints?
printf("%d\n", *(p + 2));  // What prints?
printf("%d\n", *q - *p);   // What prints?
printf("%d\n", q - p);     // What prints?
```

### Exercise 1.4 — Memory Layout
For the following program, describe the memory location of each variable:
```c
#include <stdio.h>

int global_var = 42;
static int static_var = 10;

int main() {
    int local_var = 5;
    int *heap_var = malloc(sizeof(int));
    const char *str = "hello";
    return 0;
}
```

### Exercise 1.5 — Pointer Pitfalls
Find and fix the bugs:
```c
// Bug 1
char *str = malloc(10);
strcpy(str, "this string is way too long");

// Bug 2
int *p = NULL;
*p = 42;

// Bug 3
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr;
free(p);
```

---

## Unit 2: Digital Logic

### Exercise 2.1 — Boolean Simplification
Simplify the following expressions using Boolean algebra:
- A + A·B
- A·B + A·B'
- (A + B)·(A + B')
- A'·B' + A'·B + A·B

### Exercise 2.2 — Truth Table to Gate
Design a circuit for: F(A, B, C) = Σ(0, 2, 5, 7)
- Write the truth table
- Derive the simplified SOP expression
- Draw the gate-level circuit

### Exercise 2.3 — Multiplexer Design
Build a 4:1 multiplexer using only AND, OR, and NOT gates.
- Write the truth table
- Derive the Boolean expression
- Verify with a test case: sel=2, inputs={0,1,1,0}

### Exercise 2.4 — FSM Design
Design a finite state machine that detects the sequence "101" in a serial input:
- Draw the state diagram
- Write the state transition table
- Determine the minimum number of flip-flops needed

### Exercise 2.5 — ALU Design
Design a 4-bit ALU that supports ADD, SUB, AND, OR, and XOR operations:
- Draw the block diagram
- Define the control signals
- Trace: A=5 (0101), B=3 (0011), ALUOp=ADD

---

## Unit 3: RISC-V Assembly

### Exercise 3.1 — C to Assembly
Translate to RISC-V assembly:
```c
int sum(int *arr, int n) {
    int total = 0;
    for (int i = 0; i < n; i++) {
        total += arr[i];
    }
    return total;
}
```

### Exercise 3.2 — Assembly to C
What does this assembly do?
```asm
addi sp, sp, -16
sw   ra, 12(sp)
sw   s0, 8(sp)
add  s0, zero, a0
add  t0, zero, zero
loop:
    beq  s0, zero, done
    lw   t1, 0(a0)
    add  t0, t0, t1
    addi a0, a0, 4
    addi s0, s0, -1
    j    loop
done:
    add  a0, t0, zero
    lw   s0, 8(sp)
    lw   ra, 12(sp)
    addi sp, sp, 16
    jalr zero, ra, 0
```

### Exercise 3.3 — Recursive Function
Write RISC-V assembly for factorial:
```c
int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```

### Exercise 3.4 — Calling Convention
Given this C code:
```c
int f(int a, int b) {
    int c = g(a + b);
    int d = h(c, a);
    return c + d;
}

int g(int x) { return x * 2; }
int h(int y, int z) { return y - z; }
```
Trace through the register usage for f(3, 5). Which registers hold which values at each function call?

### Exercise 3.5 — Stack Frame
Draw the stack frame for this function call:
```c
void foo(int a, int b) {
    int x = a + b;
    int y = x * 2;
    bar(x, y);
}
```
Show the stack pointer before and after the call, and label all saved registers.

---

## Unit 4: Processor Design

### Exercise 4.1 — Single-Cycle Tracing
For the instruction `lw x5, 8(x10)`, trace through the single-cycle datapath:
- What value is on the instruction memory address bus?
- What is read from the register file?
- What ALU operation is performed?
- What memory address is accessed?
- Where is the result written?

### Exercise 4.2 — Pipeline Execution
Execute the following code through a 5-stage pipeline:
```asm
add  x1, x2, x3
sub  x4, x1, x5
and  x6, x1, x7
or   x8, x6, x9
```
Fill out a pipeline diagram showing which instruction is in each stage at each cycle. Without forwarding, where are stalls needed?

### Exercise 4.3 — Data Hazards
For the same code, now with forwarding, identify:
- All RAW hazards
- Which forwarding paths resolve each hazard
- Any remaining stalls (load-use)

### Exercise 4.4 — Branch Prediction
```asm
loop:
    add  x1, x1, x2
    beq  x3, x4, done
    j    loop
done:
```
If x3 ≠ x4 for the first 8 iterations and then x3 = x4, trace the branch predictions for a 2-bit saturating counter starting in "Strongly Taken".

### Exercise 4.5 — CPI Calculation
A program has 1000 instructions:
- 40% are ALU instructions (1 cycle each)
- 30% are loads (5 cycles each)
- 20% are stores (4 cycles each)
- 10% are branches (3 cycles each)

Calculate the CPI. If pipelining reduces ALU and branch to 1 cycle each, what's the new CPI?

---

## Unit 5: Memory Hierarchy & Caches

### Exercise 5.1 — Cache Mapping
Given: 64-byte cache, 16-byte blocks, direct-mapped.
Map the following addresses to cache lines:
- 0x00
- 0x1F
- 0x20
- 0x3F
- 0x40

### Exercise 5.2 — AMAT Calculation
- L1 hit time: 1 cycle
- L1 miss rate: 5%
- L2 hit time: 10 cycles
- L2 miss rate: 20%
- Memory access time: 100 cycles

Calculate the AMAT.

### Exercise 5.3 — Cache Trace
For a 32-byte cache with 8-byte blocks (direct-mapped), trace these accesses and count hits/misses:
```
0x00, 0x04, 0x10, 0x20, 0x00, 0x08, 0x14, 0x30, 0x00
```

### Exercise 5.4 — Set-Associative Cache
For a 64-byte cache with 16-byte blocks, 2-way set-associative, LRU replacement:
- How many sets are there?
- Trace access pattern: 0x00, 0x40, 0x00, 0x80, 0x40, 0xC0
- What is the hit rate?

### Exercise 5.5 — Write Policy
Compare write-through vs write-back for this sequence (assuming 1 dirty eviction per 100 accesses):
- 100 stores to unique addresses
- 50 stores followed by 50 loads to the same addresses

Which policy performs better?

---

## Unit 6: Parallelism

### Exercise 6.1 — Amdahl's Law
A program spends 60% of its time in floating-point operations. If you can speed up the FP unit by 3×, what is the overall speedup?

### Exercise 6.2 — Speedup Analysis
A sequential program takes 100 seconds. You parallelize it such that 80% runs perfectly in parallel across N processors, and the remaining 20% is serial. What speedup do you get with:
- 2 processors?
- 4 processors?
- 8 processors?
- ∞ processors?

### Exercise 6.3 — Race Condition
Identify the race condition in this code:
```c
int counter = 0;

void* increment(void* arg) {
    for (int i = 0; i < 1000000; i++) {
        counter++;
    }
    return NULL;
}

int main() {
    pthread_t t1, t2;
    pthread_create(&t1, NULL, increment, NULL);
    pthread_create(&t2, NULL, increment, NULL);
    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
    printf("Counter: %d\n", counter); // Expected: 2000000
    return 0;
}
```
How would you fix it?

### Exercise 6.4 — Cache Coherence
Two processors share memory. Trace the coherence protocol (MSI) for:
1. P1 reads address X
2. P2 reads address X
3. P1 writes 5 to address X
4. P2 reads address X

Show the state of address X in each cache at each step.

---

## Unit 7: Virtual Memory

### Exercise 7.1 — Address Translation
Given a page size of 4KB and a 32-bit virtual address:
- How many bits are in the VPN?
- How many bits are in the offset?
- Translate virtual address 0x00003A2F with page table entry 0x00005 (PPN)

### Exercise 7.2 — TLB Walk
A 4-entry fully-associative TLB with LRU replacement processes these accesses (page numbers):
```
5, 2, 5, 8, 2, 9, 5, 8
```
Trace TLB hits and misses, updating LRU order.

### Exercise 7.3 — Page Table Size
For a 32-bit virtual address space with 4KB pages and 4-byte PTEs:
- How many pages exist?
- How large is a single-level page table?
- How large is a two-level page table (with 1KB second-level tables)?

### Exercise 7.4 — Page Replacement
With 3 physical frames and reference string: 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5
Count page faults for:
- FIFO
- LRU
- Optimal

---

## Solutions

Work through each exercise yourself before checking. Solutions should verify:
1. Your understanding of the concept
2. Your ability to trace through the system step by step
3. Your ability to connect concepts across units (e.g., how C code maps to assembly maps to hardware)
