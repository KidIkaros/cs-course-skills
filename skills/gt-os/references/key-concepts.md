# Key Concepts - Operating Systems

## 1. Process Management

### Process vs Program
- **Program**: Static code on disk (passive entity)
- **Process**: Running instance of a program (active entity)

### Process Control Block (PCB)
Contains:
- Process ID (PID)
- Process state (ready, running, waiting, terminated)
- Program counter
- CPU registers
- Memory management info (page tables, segment tables)
- I/O status information
- Accounting information
- Scheduling information (priority, queue pointers)

### Process States
```
New → Ready → Running → Terminated
              ↓    ↑
            Waiting ←→ Ready
```

### Process Creation (Unix)
```c
pid_t pid = fork();     // Creates child process
if (pid == 0) {
    // Child process
    execvp("command", args);  // Replace with new program
} else if (pid > 0) {
    // Parent process
    wait(NULL);  // Wait for child to finish
}
```

### Context Switch
- Saving state of current process
- Loading state of next process
- Overhead: 1-1000 microseconds depending on hardware

---

## 2. Scheduling Algorithms

### First Come First Served (FCFS)
- Simple queue-based scheduling
- Convoy effect: short processes wait for long ones
- Non-preemptive

### Shortest Job First (SJF)
- Optimal average waiting time
- Requires knowing burst time in advance
- Can starve long processes

### Round Robin
- Time quantum (typically 10-100ms)
- Fair allocation of CPU
- Performance depends on quantum size

### Multilevel Feedback Queues
- Multiple queues with different priorities
- Processes can move between queues
- Adapts to process behavior

### Scheduling Metrics
- **Turnaround Time**: Total time from submission to completion
- **Waiting Time**: Time spent in ready queue
- **Response Time**: Time to first response
- **Throughput**: Processes completed per unit time

---

## 3. Synchronization Primitives

### Race Condition
Two or more processes accessing shared data concurrently, result depends on execution order.

### Critical Section Problem
Requirements:
1. **Mutual Exclusion**: Only one process in critical section
2. **Progress**: No deadlock
3. **Bounded Waiting**: No starvation

### Mutex Lock
```c
pthread_mutex_t lock;
pthread_mutex_init(&lock, NULL);

pthread_mutex_lock(&lock);
// Critical section
pthread_mutex_unlock(&lock);
```

### Semaphores
```c
sem_t sem;
sem_init(&sem, 0, 1);  // Binary semaphore

sem_wait(&sem);   // Decrement (P operation)
// Critical section
sem_post(&sem);   // Increment (V operation)
```

### Monitors
- High-level synchronization construct
- Encapsulates shared data with procedures
- Only one process active at a time
- Uses condition variables for signaling

### Condition Variables
```c
pthread_cond_t cond;
pthread_cond_init(&cond, NULL);

pthread_mutex_lock(&lock);
while (!condition) {
    pthread_cond_wait(&cond, &lock);  // Release lock, sleep
}
// Do work
pthread_mutex_unlock(&lock);
```

---

## 4. Deadlock

### Four Conditions (Coffman)
1. **Mutual Exclusion**: Resources are non-sharable
2. **Hold and Wait**: Process holds while waiting
3. **No Preemption**: Resources cannot be taken away
4. **Circular Wait**: Circular chain of processes waiting

### Prevention
- Eliminate one of the four conditions
- Example: Require all resources at once (no hold and wait)

### Avoidance (Banker's Algorithm)
- Safe state: System can allocate resources without deadlock
- Check if allocation leaves system in safe state
- Requires advance knowledge of max resource needs

### Detection and Recovery
- Allow deadlocks to occur
- Periodically check for cycles in resource graph
- Recovery: Terminate processes or preempt resources

---

## 5. Memory Management

### Address Translation
- Logical address → Physical address
- Done by Memory Management Unit (MMU)

### Contiguous Allocation
- Each process gets single contiguous block
- Problem: External fragmentation

### Segmentation
- Process divided into logical segments
- Each segment has base and limit
- Supports logical division of address space

### Paging
- Fixed-size blocks (pages)
- No external fragmentation
- Page table maps logical to physical pages

### Page Table Entry (PTE)
```
| Valid | Dirty | Reference | Protection | Frame Number |
```

### Translation Lookaside Buffer (TLB)
- Cache for page table entries
- Reduces memory access time
- TLB miss requires page table lookup

---

## 6. Virtual Memory

### Demand Paging
- Pages loaded only when needed
- Reduces memory footprint
- Page fault: Page not in memory

### Page Replacement Algorithms

#### FIFO (First In First Out)
- Replace oldest page
- Belady's anomaly: More frames can cause more faults

#### LRU (Least Recently Used)
- Replace page not used for longest time
- Good approximation of optimal
- Implementation: Counter or stack

#### Clock (Second Chance)
- Circular buffer with reference bit
- If ref bit = 1, give second chance
- Approximation of LRU

#### Optimal
- Replace page not needed for longest time
- Impossible to implement (requires future knowledge)
- Benchmark for other algorithms

### Thrashing
- Excessive page faults
- System spends more time paging than executing
- Solution: Working set model

### Working Set
- Set of pages actively being used
- Keep working set in memory
- Adjust degree of multiprogramming

---

## 7. File Systems

### Inode Structure
- Index node: Metadata for file
- Contains:
  - File size
  - Owner/permissions
  - Timestamps
  - Direct/indirect block pointers

### File Allocation Methods

#### Contiguous
- File stored in consecutive blocks
- Fast sequential access
- External fragmentation

#### Linked
- Each block points to next
- No external fragmentation
- Slow random access

#### Indexed
- Index block contains pointers to data blocks
- Supports random access
- Extra space for index

### Directory Implementation
- Linear list: Simple but slow
- Hash table: Fast lookup
- B-tree: Balanced performance

### RAID (Redundant Array of Independent Disks)
| Level | Description | Fault Tolerance |
|-------|-------------|-----------------|
| 0 | Striping | None |
| 1 | Mirroring | 1 disk |
| 5 | Distributed parity | 1 disk |
| 6 | Double parity | 2 disks |
| 10 | Stripe + Mirror | Multiple |

---

## 8. I/O Systems

### I/O Methods
- **Programmed I/O**: CPU busy-waits
- **Interrupt-driven I/O**: CPU does other work
- **DMA**: Hardware handles transfer

### Buffering
- Temporary storage for data in transit
- Handles speed mismatch
- Single, double, circular buffering

### Caching
- Store frequently accessed data
- Faster than original location
- Cache coherence problem

### Disk Scheduling
- Minimize seek time and rotational latency
- Algorithms: FCFS, SSTF, SCAN, C-SCAN
