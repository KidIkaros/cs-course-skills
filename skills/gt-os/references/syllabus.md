# CS 6200 - Introduction to Operating Systems

**University**: Georgia Institute of Technology  
**Platform**: Udacity (Free)  
**Level**: Intermediate-Advanced  
**URL**: https://www.udacity.com/course/introduction-to-operating-systems--ud923

---

## Course Structure

### Module 1: Introduction and Processes
- What is an operating system?
- OS as a resource manager
- Process abstraction and lifecycle
- Process control block (PCB)
- Process creation: fork(), exec(), wait()
- Process termination and zombies

### Module 2: Process Scheduling
- CPU scheduling goals (throughput, latency, fairness)
- Scheduling algorithms:
  - First Come First Served (FCFS)
  - Shortest Job First (SJF)
  - Priority scheduling
  - Round Robin
  - Multilevel Feedback Queues
- Context switching overhead
- Preemptive vs cooperative scheduling

### Module 3: Threads and Concurrency
- Process vs thread distinction
- User-level threads vs kernel threads
- POSIX threads (pthreads) API
- Thread creation, joining, and detachment
- Thread-local storage
- Benefits and challenges of multithreading

### Module 4: Synchronization
- Race conditions and critical sections
- Mutex locks
- Semaphores (binary and counting)
- Monitors and condition variables
- Readers-writers problem
- Producer-consumer problem
- Dining philosophers problem

### Module 5: Deadlocks
- Deadlock conditions (Coffman conditions)
- Deadlock detection and recovery
- Deadlock prevention strategies
- Deadlock avoidance (Banker's algorithm)
- Resource allocation graphs

### Module 6: Memory Management
- Address spaces and address translation
- Memory allocation strategies
  - Fixed partitioning
  - Variable partitioning
  - Buddy system
- Segmentation
- Fragmentation (internal vs external)
- Swapping

### Module 7: Virtual Memory
- Demand paging concept
- Page tables and page table entries
- Translation Lookaside Buffer (TLB)
- Multi-level page tables
- Inverted page tables
- Page replacement algorithms:
  - Optimal (Belady's)
  - FIFO
  - Least Recently Used (LRU)
  - Clock (Second Chance)
  - LFU/MFU
- Working set model
- Thrashing

### Module 8: File Systems
- File abstraction and operations
- Directory structure and implementation
- Inode structure and allocation
- File system mounting
- File allocation methods:
  - Contiguous
  - Linked
  - Indexed
- Free space management
- Journaling and log-structured file systems
- RAID levels (0, 1, 5, 6, 10)

### Module 9: I/O Systems
- I/O hardware and device drivers
- Polling vs interrupts
- DMA (Direct Memory Access)
- Buffering and caching
- Disk scheduling algorithms:
  - FCFS
  - SSTF
  - SCAN (Elevator)
  - C-SCAN
- Disk structure and geometry
- Solid-state drives (SSDs) vs HDDs

---

## Assessment Components

- **Quizzes**: Knowledge checks after each module
- **Programming Assignments**: Hands-on C/C++ implementations
- **Midterm Exam**: Covers first half of course
- **Final Exam**: Comprehensive

## Time Commitment

- Estimated 8-12 hours per week
- Course duration: Approximately 15 weeks
