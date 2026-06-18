# MIT 6.1810 - Lab Exercises and Practice Problems

## Lab Assignments

### Lab 1: Sleep
**Objective:** Implement the `sleep` system call.

**Tasks:**
1. Add `sleep` to `user/user.h`
2. Add `sleep` to `user/usys.pl`
3. Implement `sys_sleep()` in `kernel/sysproc.c`
4. Handle edge cases (sleep 0, sleep negative)

**Hints:**
- Use `ticks` and `ticksleep()` or `tsleep()`
- Understand how interrupts wake sleeping processes
- Test with `sleep 10` in xv6 shell

---

### Lab 2: Find
**Objective:** Implement a file search utility.

**Tasks:**
1. Recursively traverse directory tree
2. Search for files matching a pattern
3. Handle both files and directories

**Hints:**
- Use `stat()` to get file info
- Use `readdir()` to iterate directory entries
- Recursive traversal with depth tracking

---

### Lab 3: Xargs
**Objective:** Implement the `xargs` utility.

**Tasks:**
1. Read lines from stdin
2. Append each line as arguments to a command
3. Execute the command with appended arguments

**Hints:**
- Parse input lines carefully
- Use `exec()` to run commands
- Handle argument boundaries

---

### Lab 4: Trace
**Objective:** Implement system call tracing.

**Tasks:**
1. Add `trace` system call
2. Accept bitmask of system calls to trace
3. Print trace output on each traced call
4. Implement `trace` user command

**Hints:**
- Modify `syscall()` in `kernel/syscall.c`
- Add trace mask to `struct proc`
- Print format: `pid: syscall_name -> arg1, arg2`

---

### Lab 5: Postgres
**Objective:** Understand user-space memory access.

**Tasks:**
1. Trace memory accesses in user program
2. Understand page faults and memory mapping
3. Analyze virtual → physical translations

**Hints:**
- Use `/proc/self/maps` equivalent
- Understand user page table structure
- Track memory allocations

---

### Lab 6: Utilities
**Objective:** Implement user-level utilities.

**Tasks:**
1. Implement `uptime` command
2. Implement `uptime` system call
3. Handle edge cases

**Hints:**
- Similar to sleep lab structure
- Understand system call mechanism

---

### Lab 7: Pingpong
**Objective:** IPC with pipes.

**Tasks:**
1. Parent writes to child, child reads and writes back
2. Parent reads child's response
3. Ping-pong communication pattern

**Hints:**
- Use `pipe()` to create pipe pairs
- `fork()` to create child
- Close unused pipe ends

---

### Lab 8: Primes
**Objective:** Parallel prime sieve.

**Tasks:**
1. Implement Sieve of Eratosthenes
2. Each prime filter runs in separate process
3. Pipes connect filter processes

**Hints:**
- Process for each prime
- Parent sends numbers, child filters and forwards
- Properly close pipes to avoid deadlocks

---

### Lab 9: Find (Advanced)
**Objective:** Recursive file search with pattern matching.

**Tasks:**
1. Search for files by name pattern
2. Search for files by type (file, directory, link)
3. Handle symbolic links

**Hints:**
- Use `lstat()` instead of `stat()` for symlinks
- Pattern matching with wildcards

---

### Lab 10: Xargs (Advanced)
**Objective:** Batch argument processing.

**Tasks:**
1. Read multiple lines from input
2. Execute command with accumulated arguments
3. Handle argument limits

**Hints:**
- Buffer input lines
- Split on whitespace/newlines
- Execute after buffer full or EOF

---

### Lab 11: Locks
**Objective:** Implement spin locks.

**Tasks:**
1. Implement `acquire()` and `release()`
2. Disable interrupts during lock hold
3. Add debugging information
4. Test for correctness

**Hints:**
- Use `__sync_lock_test_and_set()` or similar atomic
- Remember to disable interrupts in kernel
- Lock ordering prevents deadlocks

---

### Lab 12: Scheduler
**Objective:** Implement a scheduling algorithm.

**Tasks:**
1. Implement round-robin scheduler
2. Add priority support
3. Implement time quantum

**Hints:**
- Modify `scheduler()` in `kernel/proc.c`
- Understand process states
- Use timer interrupts for preemption

---

### Lab 13: Interrupts
**Objective:** Implement interrupt handling.

**Tasks:**
1. Register interrupt handlers
2. Implement deferred processing
3. Handle nested interrupts

**Hints:**
- Understand trap frame
- Use bottom halves for deferred work
- Properly save/restore state

---

### Lab 14: Copy-on-Write (COW)
**Objective:** Implement COW fork.

**Tasks:**
1. Share pages between parent and child (read-only)
2. On write fault, allocate new page and copy
3. Update page table entry

**Hints:**
- Add COW bit to PTE flags
- Handle page fault in `usertrap()`
- Reference counting for pages

---

### Lab 15: Signals
**Objective:** Implement signal handling.

**Tasks:**
1. Implement `sigaction()` system call
2. Deliver signals to processes
3. Handle signal masks and blocking
4. Implement `sigreturn()`

**Hints:**
- Modify trap frame for signal delivery
- Save/restore signal context
- Handle pending signals

---

### Lab 16: Swapper
**Objective:** Implement memory swapping.

**Tasks:**
1. Write pages to disk when memory is low
2. Read pages back on access fault
3. Implement page replacement policy

**Hints:**
- Use disk as swap space
- Implement page eviction algorithm
- Handle page-in and page-out

---

### Lab 17: Crash Recovery
**Objective:** Improve file system crash recovery.

**Tasks:**
1. Implement write-ahead logging
2. Recover from simulated crashes
3. Ensure consistency

**Hints:**
- Understand log structure
- `begin_op()` / `end_op()` pattern
- Replay log on mount

---

## Practice Problems

### Problem 1: Address Translation
Given a page table, translate virtual addresses to physical addresses.

**Example:**
```
Page Table:
VPN 0x1 → PPN 0x5, Valid=1, R=1, W=0, X=1
VPN 0x2 → PPN 0x3, Valid=1, R=1, W=1, X=0

Translate 0x1234:
VPN = 0x1, Offset = 0x234
Physical = 0x5234
```

### Problem 2: Context Switch Analysis
Calculate context switch overhead given register save/restore times.

### Problem 3: Page Table Walk
Trace through a multi-level page table walk for a given virtual address.

### Problem 4: File System Layout
Given an inode structure, calculate how many blocks a file can reference.

### Problem 5: Deadlock Detection
Identify deadlocks in given resource allocation graphs.

### Problem 6: Scheduling Analysis
Calculate turnaround time and waiting time for different scheduling algorithms.

### Problem 7: Lock Ordering
Determine if a given lock acquisition sequence can deadlock.

### Problem 8: Pipe Behavior
Predict behavior of pipe operations with blocking/non-blocking modes.

### Problem 9: System Call Tracing
Analyze system call traces to understand program behavior.

### Problem 10: Memory Allocation
Calculate fragmentation for different allocation strategies.

---

## Debugging Checklist

- [ ] Check for null pointer dereferences
- [ ] Verify lock acquisition order
- [ ] Ensure proper memory deallocation
- [ ] Check for race conditions
- [ ] Verify system call argument validation
- [ ] Test edge cases (0, max, negative)
- [ ] Check for deadlocks
- [ ] Verify file system consistency
- [ ] Test crash recovery
- [ ] Check for memory leaks

---

## Tips for Success

1. **Read the xv6 book** before each lab
2. **Understand the code** before modifying it
3. **Test incrementally** - don't write everything at once
4. **Use gdb** for kernel debugging
5. **Check invariants** at each step
6. **Read error messages** carefully
7. **Ask questions** on Piazza
8. **Start early** - labs build on each other
9. **Document your changes** as you go
10. **Test with multiple scenarios**
