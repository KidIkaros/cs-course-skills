# MIT 6.1810 - Operating System Engineering Syllabus

**Course:** 6.1810 Operating System Engineering
**Semester:** Fall 2023
**Instructors:** Robert Morris, Adam Belay
**Institution:** MIT

## Course Description

This course covers the design and implementation of operating systems. Topics include virtual memory, file systems, threads, context switches, kernels, interrupts, system calls, inter-process communication, and related topics. Through a series of labs, students build and modify a small operating system (xv6) to understand how these concepts are implemented in practice.

## Prerequisites

- 6.1910 (Computation Structures) or equivalent
- Strong C programming skills
- Familiarity with assembly language (RISC-V or x86)
- Understanding of basic computer architecture

## Topics Covered

### Unit 1: Introduction and Tools
- Course overview and logistics
- xv6 and RISC-V architecture overview
- Build tools and debugging with QEMU + GDB

### Unit 2: Operating System Organization
- Kernel and user mode
- System calls and traps
- Process organization
- xv6 kernel structure

### Unit 3: Page Tables
- Virtual address spaces
- Multi-level page tables
- TLB and address translation
- Kernel page table setup
- Lab: Print kernel page table

### Unit 4: Traps and System Calls
- Trap vectors and trap frames
- System call mechanism
- Lab: Implement trace system call
- User/kernel boundary

### Unit 5: Interrupts
- Device interrupts and interrupt handlers
- Deferred work and bottom halves
- Lab: Implement interrupt handling

### Unit 6: Scheduling
- Process states and transitions
- Context switching
- Scheduling algorithms (Round Robin, MLFQ)
- Lab: Implement scheduler

### Unit 7: Locking
- Spin locks
- Sleep locks
- Lock ordering and deadlocks
- Lab: Implement locks

### Unit 8: Scheduling (Advanced)
- Multi-level feedback queue
- Per-CPU scheduling
- SMP scheduling issues

### Unit 9: File Systems
- Inodes and disk layout
- Directories and path resolution
- Logging and crash recovery
- Lab: Implement symbolic links

### Unit 10: Crash Recovery and File System Performance
- Write-ahead logging
- Journaling
- File system performance optimization

### Unit 11: Interrupts and Bottom Halves
- Deferred interrupt processing
- Tasklets and work queues
- Lab: Implement interrupt handling

### Unit 12: Virtual Memory (Advanced)
- Demand paging
- Copy-on-write
- Memory-mapped files
- Lab: Implement copy-on-write fork

### Unit 13: User-Level Features
- Signals
- Process groups
- Lab: Implement signals

### Unit 14: Locking (Advanced)
- Reader-writer locks
- Lock-free data structures
- Memory ordering and barriers

### Unit 15: Virtual Memory (Advanced)
- Swapping
- Memory allocation strategies
- Lab: Implement swapper

### Unit 16: Scheduling (Review)
- Review of scheduling concepts
- MLFQ in depth

### Unit 17: File System (Advanced)
- Extended attributes
- Large file support
- NFS and distributed file systems

### Unit 18: Crash Recovery (Advanced)
- Soft updates
- Metadata consistency
- Lab: Improve crash recovery

### Unit 19: Performance and Tuning
- Performance measurement tools
- Optimization strategies
- Kernel profiling

### Unit 20: Security
- Access control
- Capabilities
- Security in operating systems

### Unit 21: Virtualization
- Containers and namespaces
- Hypervisors
- Virtual machine monitors

### Unit 22: Parallelism
- SMP and multicore
- Parallel algorithms
- Lock-free programming

### Unit 23: Distributed Systems
- RPC and communication
- Distributed file systems
- Consensus and replication

### Unit 24: Course Review
- Comprehensive review
- Final exam preparation

## Grading

- Labs: 50%
- Quizzes: 20%
- Final Exam: 30%

## Lab Assignments

| Lab | Topic | Description |
|-----|-------|-------------|
| 1 | Sleep | Implement sleep system call |
| 2 | Find | File system traversal utility |
| 3 | Xargs | Argument processing |
| 4 | Trace | System call tracing |
| 5 | Postgres | User-space memory access |
| 6 | Utilities | User-level tools |
| 7 | Pingpong | IPC with pipes |
| 8 | Primes | Parallel prime sieve |
| 9 | Find | Recursive file search |
| 10 | Xargs | Batch argument processing |
| 11 | Locks | Implement spin locks |
| 12 | Scheduler | Implement scheduler |
| 13 | Interrupts | Interrupt handling |
| 14 | COW | Copy-on-write fork |
| 15 | Signals | Signal handling |
| 16 | Swapper | Memory swapping |
| 17 | Crash Recovery | File system crash recovery |

## Resources

- xv6 Book: https://pdos.csail.mit.edu/6.828/2023/xv6/book-riscv-rev1.pdf
- xv6 Source: https://github.com/mit-pdos/xv6-riscv
- OCW Page: https://ocw.mit.edu/courses/6-1810-operating-system-engineering-fall-2023/
- Piazza Discussion: (course Piazza page)

## Academic Integrity

All work must be your own. Collaboration is encouraged for discussion, but all submitted code must be written individually. Plagiarism or copying code from any source (including AI tools) is prohibited.
