# Resources - Operating Systems

## Primary Course Materials

### Udacity Course
- **Course**: CS 6200 - Introduction to Operating Systems
- **URL**: https://www.udacity.com/course/introduction-to-operating-systems--ud923
- **Instructor**: Dr. Ada Gavrilovska (Georgia Tech)
- **Format**: Free video lectures, quizzes, programming assignments

### Course Lectures
1. Introduction to OS
2. Processes
3. Process Creation
4. Process Termination
5. Process States
6. Process Scheduling
7. Scheduling Algorithms
8. Scheduling Examples
9. Thread Introduction
10. Thread API
11. Thread Issues
12. Locks
13. Semaphores
14. Monitors
15. Deadlock Introduction
16. Deadlock Prevention
17. Deadlock Avoidance
18. Deadlock Detection
19. Memory Introduction
20. Address Spaces
21. Memory Allocation
22. Segmentation
23. Paging
24. Page Tables
25. TLB
26. Intro to Virtual Memory
27. Page Replacement
28. Thrashing
29. File System Introduction
30. File System Implementation
31. Directory Implementation
32. File System Management
33. RAID
34. I/O Introduction
35. I/O Devices
36. Disk Drives
37. Disk Scheduling

---

## Textbooks

### Primary Textbook
**Operating Systems: Three Easy Pieces**
- Authors: Remzi Arpaci-Dusseau, Andrea Arpaci-Dusseau
- URL: https://pages.cs.wisc.edu/~remzi/OSTEP/
- Cost: Free online
- Covers: Processes, threads, virtual memory, concurrency, persistence

### Supplementary Textbooks
1. **Operating System Concepts** (Dinosaur Book)
   - Authors: Silberschatz, Galvin, Gagne
   - 10th Edition
   - Comprehensive reference

2. **Modern Operating Systems**
   - Author: Andrew Tanenbaum
   - 4th Edition
   - Good for distributed systems

3. **Operating Systems: Design and Implementation**
   - Author: Andrew Tanenbaum
   - Based on MINIX
   - Practical implementation focus

---

## Online Resources

### Tutorials and Guides
- **Beej's Guide to Unix IPC**: https://beej.us/guide/bgipc/
- **Pthreads Tutorial**: https://www.cs.cmu.edu/afs/cs/academic/class/15492-f07/www/pthreads.html
- **The Linux Programming Interface**: https://man7.org/linux/man-pages/

### Interactive Simulations
- **OS/161 Simulator**: https://os161.teach.cs.toronto.edu/
- **Virtual Machine Lab**: Use VirtualBox or VMware for hands-on practice
- **Process Scheduling Simulator**: https://boonsuen.com/process-scheduling-solver

### Video Lectures
- **MIT 6.004**: Computation Structures (YouTube)
- **Berkeley CS162**: Operating Systems (YouTube)
- **Stanford CS140**: Operating Systems

---

## Programming Resources

### C/C++ Development
- **GCC Compiler**: https://gcc.gnu.org/
- **GDB Debugger**: https://www.gnu.org/software/gdb/
- **Valgrind**: https://valgrind.org/
- **Strace**: System call tracer

### POSIX APIs
- **fork(2)**: Create process
- **exec(3)**: Execute program
- **wait(2)**: Wait for process
- **pthread(7)**: POSIX threads
- **sem_overview(7)**: Semaphores
- **shm_overview(7)**: Shared memory

### Development Environment
```bash
# Ubuntu/Debian
sudo apt-get install build-essential gdb valgrind strace

# Compile with threading
gcc -pthread -o program program.c

# Debug
gdb ./program

# Memory check
valgrind --leak-check=full ./program

# Trace system calls
strace ./program
```

---

## Practice Problems

### Scheduling Algorithms
- **CPU Scheduling Simulator**: Practice FCFS, SJF, RR, MLFQ
- Calculate turnaround time, waiting time, response time
- Compare algorithms with different workloads

### Synchronization
- **Producer-Consumer Problem**: Classic bounded buffer
- **Readers-Writers Problem**: Multiple readers, exclusive writers
- **Dining Philosophers**: Resource allocation and deadlock

### Memory Management
- **Page Replacement Simulator**: Compare FIFO, LRU, Optimal
- **TLB Simulation**: Calculate effective access time
- **Memory Allocation**: Implement first-fit, best-fit, worst-fit

### File Systems
- **Inode Simulation**: Implement basic file operations
- **Disk Scheduling**: Compare FCFS, SSTF, SCAN, C-SCAN
- **RAID Calculator**: Calculate performance and redundancy

---

## Reference Cards

### System Call Reference
```c
// Process
pid_t fork(void);
int execvp(const char *file, char *const argv[]);
pid_t wait(int *status);
void exit(int status);

// Threads
int pthread_create(pthread_t *thread, const pthread_attr_t *attr,
                   void *(*start_routine)(void*), void *arg);
int pthread_join(pthread_t thread, void **retval);
int pthread_mutex_init(pthread_mutex_t *mutex, const pthread_mutexattr_t *attr);
int pthread_mutex_lock(pthread_mutex_t *mutex);
int pthread_mutex_unlock(pthread_mutex_t *mutex);

// Semaphores
int sem_init(sem_t *sem, int pshared, unsigned int value);
int sem_wait(sem_t *sem);
int sem_post(sem_t *sem);
int sem_destroy(sem_t *sem);
```

### Key Formulas
- **CPU Utilization**: (Time CPU is busy) / (Total time)
- **Throughput**: Number of processes completed / Time period
- **Turnaround Time**: Completion time - Arrival time
- **Waiting Time**: Turnaround time - Burst time
- **Response Time**: Time to first response
- **Effective Access Time**: (TLB hit rate × TLB access time) + (TLB miss rate × (TLB access time + Memory access time))

---

## Community and Forums

### Discussion Forums
- **Udacity Forums**: Course-specific discussions
- **Reddit**: r/os, r/learnprogramming
- **Stack Overflow**: Tags: [operating-system], [pthreads], [fork]

### Study Groups
- **Georgia Tech OMSCS**: Online Master of Science in Computer Science
- **Study Group Discord**: Many study groups available

### Office Hours
- **Udacity**: Check course page for schedule
- **Georgia Tech**: For enrolled students

---

## Tools and Software

### Virtual Machines
- **VirtualBox**: Free, cross-platform
- **VMware Workstation Player**: Free for personal use
- **QEMU**: Advanced emulator

### Linux Distributions for OS Study
- **Ubuntu**: User-friendly, good for beginners
- **Fedora**: Cutting-edge features
- **Arch Linux**: DIY approach, learn by building
- **Linux From Scratch**: Ultimate learning experience

### Debugging Tools
- **GDB**: GNU Debugger
- **Valgrind**: Memory debugging, leak detection
- **strace**: System call tracing
- **ltrace**: Library call tracing
- **DTrace**: Dynamic tracing framework
- ** perf**: Linux profiling tool
