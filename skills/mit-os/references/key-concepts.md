# Key Concepts - MIT 6.1810 Operating System Engineering

## 1. Virtual Memory

### Address Spaces
- Each process has its own virtual address space
- Virtual addresses are translated to physical addresses by the MMU
- Provides isolation between processes
- Enables memory overcommitment

### Page Tables
- Multi-level structures mapping virtual → physical pages
- Each entry contains: physical page number, valid bit, permission bits (R/W/X)
- RISC-V Sv39: 3-level page tables, 39-bit virtual addresses
- Page size: 4KB (2^12 bytes)

### Address Translation
```
Virtual Address = [VPN | Offset]
VPN → Page Table Walk → PPN
Physical Address = [PPN | Offset]
```

### TLB (Translation Lookaside Buffer)
- Hardware cache for page table entries
- TLB misses cause page table walks
- TLB flush required on context switch (or use ASID)

### Kernel vs User Page Tables
- Kernel page table: identity-maps all physical memory
- User page table: maps only user pages, kernel pages marked no-access
- Kernel memory protected from user access

### Key Functions
```c
// xv6 page table functions
pagetable_t create();
void free(pagetable_t);
int mappages(pagetable_t, uint64 va, uint64 pa, uint64 sz, int perm);
pte_t *walk(pagetable_t, uint64 va, int alloc);
void uvmunmap(pagetable_t, uint64 va, uint64 npages);
```

## 2. File Systems

### On-Disk Structure
```
Block 0: Boot block
Block 1: Superblock (size, inode count, etc.)
Block 2+: Log blocks (for crash recovery)
Then: Inode blocks
Then: Bitmap blocks (free block tracking)
Then: Data blocks
```

### Inodes
- Index node: metadata for a file
- Contains: size, block addresses (direct + indirect), type, permissions
- Inode number is the file's unique identifier
- In-memory inode adds: reference count, lock, dirty flag

### Directories
- Special files mapping names → inode numbers
- Root directory is inode 2
- "." and ".." are directory entries

### Path Resolution
1. Start at root inode
2. Parse path components left-to-right
3. For each component, look up in current directory
4. Follow to next inode

### Logging (Write-Ahead Logging)
- All writes logged before committing
- On crash, replay log to recover
- Ensures atomicity of multi-block operations
- `begin_op()` / `end_op()` bracket log transactions

### Key Functions
```c
// xv6 file system functions
uint32 ialloc(uint16 type);          // Allocate new inode
struct inode* idup(struct inode*);    // Increment ref count
void ilock(struct inode*);            // Lock inode
void iunlock(struct inode*);          // Unlock inode
void iput(struct inode*);             // Release inode
int readi(struct inode*, int, uint64, uint, uint);
int writei(struct inode*, int, uint64, uint, uint);
```

## 3. Processes and Threads

### Process States
```
UNUSED → SLEEPING → RUNNABLE → RUNNING → (exit/zombie)
```

### Process Control Block (PCB)
```c
struct proc {
    uint64 state;        // Process state
    uint64 pid;          // Process ID
    uint64 parent;       // Parent PID
    uint64 kstack;       // Kernel stack pointer
    uint64 pagetable;    // Page table
    struct context *context;  // Saved registers
    // ... more fields
};
```

### Context Switching
1. Save current process registers to its PCB
2. Switch kernel stacks
3. Restore new process registers from its PCB
4. Resume execution at saved PC

### Process Creation
```c
// fork() creates child process
// 1. Allocate new proc structure
// 2. Copy parent's page table (COW in lab 14)
// 3. Copy register state
// 4. Set child PID, parent PID
// 5. Place child in RUNNABLE queue

// exec() replaces process image
// 1. Parse ELF binary
// 2. Create new page table
// 3. Load segments into new pages
// 4. Set up user stack
// 5. Jump to entry point
```

### Threads vs Processes
- Thread: execution context within a process
- Process: container with address space + threads
- xv6 has one thread per process (no user threads)
- Context switch is between kernel threads

## 4. Kernel Architecture

### Monolithic Kernel
- All OS services in kernel space
- Direct function calls between subsystems
- xv6 is a simplified monolithic kernel
- Linux is a monolithic kernel with modules

### Microkernel
- Minimal kernel: IPC, scheduling, memory management
- File systems, drivers in user space
- More isolation, more overhead
- Examples: MINIX, seL4, Fuchsia

### Kernel/User Boundary
- User mode: restricted instructions, limited memory access
- Kernel mode: full hardware access
- Transitions via traps (syscall, interrupt, exception)
- Hardware enforces the boundary

### System Call Mechanism
```
User Space                    Kernel Space
   |                              |
   | syscall instruction          |
   | --------→ Save registers ----|
   |          Switch to kernel    |
   |          Stack               |
   |          Dispatch to handler |
   |          Execute handler     |
   |          Restore registers   |
   | ←-------- Return value ------|
   |                              |
```

### Interrupt Handling
1. Hardware raises interrupt
2. CPU saves minimal state
3. Jump to interrupt vector
4. Save full register state
5. Call interrupt handler
6. Handle deferred work
7. Restore and return

## 5. Concurrency and Synchronization

### Race Conditions
- Multiple threads accessing shared data
- Outcome depends on timing
- Bugs are non-deterministic

### Mutual Exclusion
- Locks ensure only one thread accesses critical section
- Spin lock: busy-wait until lock acquired
- Sleep lock: block until lock available

### Deadlock
Four conditions (all must hold):
1. Mutual exclusion
2. Hold and wait
3. No preemption
4. Circular wait

Prevention: enforce lock ordering

### Spin Locks in xv6
```c
struct spinlock {
    uint locked;       // Lock status
    uint pid;          // Holding CPU's PID (for debugging)
    char *name;        // Lock name
};

void acquire(struct spinlock *lock);  // Acquire lock
void release(struct spinlock *lock);  // Release lock
```

### Sleep/Wakeup
- `sleep(chan, lock)`: release lock, wait on channel, reacquire
- `wakeup(chan)`: wake all sleepers on channel
- Prevents missed wakeups

## 6. Inter-Process Communication

### Pipes
- Unidirectional byte stream
- Kernel buffer connects reader and writer
- `pipe(fd[2])` creates pipe
- `fd[0]` = read end, `fd[1]` = write end

### Signals
- Software interrupts delivered to processes
- Signal handlers registered with `sigaction()`
- Default actions: terminate, stop, ignore
- Signals can interrupt blocked system calls

### Shared Memory
- Multiple processes map same physical pages
- Fast but requires synchronization
- No built-in IPC mechanism in xv6

## 7. System Calls in xv6

### Common System Calls
| Call | Description |
|------|-------------|
| `fork()` | Create child process |
| `exit()` | Terminate process |
| `wait()` | Wait for child |
| `exec()` | Replace process image |
| `read()` | Read from file descriptor |
| `write()` | Write to file descriptor |
| `open()` | Open file |
| `close()` | Close file descriptor |
| `pipe()` | Create pipe |
| `sbrk()` | Grow/shrink memory |
| `kill()` | Send signal to process |
| `getpid()` | Get process ID |
| `sleep()` | Sleep for duration |
| `uptime()` | Get system uptime |
| `trace()` | Trace system calls (lab 4) |

### System Call Dispatch
```c
// kernel/syscall.c
static uint64 syscalls[] = {
    [SYS_fork] sys_fork,
    [SYS_exit] sys_exit,
    [SYS_wait] sys_wait,
    // ... etc
};

void syscall(void) {
    int num = p->trapframe->a7;  // System call number
    // ... validate and dispatch
}
```

## 8. Memory Management

### Physical Memory Allocation
- Simple buddy allocator or free list
- Page-granularity (4KB)
- `kalloc()` / `kfree()` for kernel pages

### Virtual Memory Layout (RISC-V xv6)
```
Kernel space: 0x80000000 → end of RAM (identity mapped)
User space:   0 → 0x80000000 (text, data, stack, heap)
```

### Copy-on-Write (COW)
- Fork shares parent's pages (read-only)
- On write fault, allocate new page, copy, update PTE
- Saves memory for short-lived children

### Swapping
- Move inactive pages to disk
- Page fault brings them back
- Requires free page replacement policy

## 9. File System Operations

### Opening a File
1. `open(path, flags)` → file descriptor
2. Resolve path → inode number
3. Allocate file descriptor in process
4. Return fd to user

### Reading/Writing
1. `read(fd, buf, n)` → bytes read
2. Look up fd → inode
3. `readi(inode, user_dst, dst, n, offset)`
4. Follow indirect blocks if needed
5. Copy data to user buffer

### File Descriptor Table
```c
struct proc {
    struct file *ofile[NOFILE];  // Open files
    // ...
};

struct file {
    enum { FD_NONE, FD_PIPE, FD_INODE } type;
    int ref;          // Reference count
    struct inode *ip; // Underlying inode
    uint off;         // File offset
    // ...
};
```

## 10. Debugging xv6

### QEMU + GDB
```bash
# Start QEMU with GDB server
make qemu-gdb

# In another terminal
gdb
(gdb) target remote localhost:26000
(gdb) b kerneltrap
(gdb) c
```

### Common Debugging Commands
```bash
(gdb) info registers      # Show registers
(gdb) x/10x $sp          # Examine stack
(gdb) bt                 # Backtrace
(gdb) p proc             # Print proc struct
(gdb) info page_table     # Show page tables
```

### Print Debugging
```c
printf("DEBUG: pid=%d, state=%d\n", p->pid, p->state);
```

### Kernel Panics
- `panic("message")` halts the kernel
- Use for invariant violations
- Often caused by null pointer dereference, double free, etc.
