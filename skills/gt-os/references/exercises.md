# Exercises - Operating Systems

## Exercise 1: Process Creation

**Objective**: Understand fork() and exec() system calls.

**Task**: Write a C program that:
1. Creates a child process using `fork()`
2. Child executes `ls -la` using `execvp()`
3. Parent waits for child to complete
4. Print PID of both parent and child

**Expected Output**:
```
Parent PID: 12345
Child PID: 12346
[output of ls -la]
Child process completed with status: 0
```

**Solution Pattern**:
```c
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    pid_t pid = fork();
    
    if (pid < 0) {
        perror("fork failed");
        return 1;
    } else if (pid == 0) {
        // Child
        char *args[] = {"ls", "-la", NULL};
        execvp("ls", args);
        perror("exec failed");
    } else {
        // Parent
        printf("Parent PID: %d\n", getpid());
        printf("Child PID: %d\n", pid);
        int status;
        wait(&status);
        printf("Child completed with status: %d\n", WEXITSTATUS(status));
    }
    return 0;
}
```

---

## Exercise 2: Thread Synchronization

**Objective**: Implement thread-safe counter using mutexes.

**Task**: Write a C program that:
1. Creates 10 threads
2. Each thread increments a shared counter 1000 times
3. Use mutex to protect critical section
4. Verify final counter value is 10000

**Expected Output**:
```
Final counter value: 10000
```

**Solution Pattern**:
```c
#include <stdio.h>
#include <pthread.h>

#define NUM_THREADS 10
#define INCREMENTS 1000

int counter = 0;
pthread_mutex_t lock;

void* increment(void* arg) {
    for (int i = 0; i < INCREMENTS; i++) {
        pthread_mutex_lock(&lock);
        counter++;
        pthread_mutex_unlock(&lock);
    }
    return NULL;
}

int main() {
    pthread_t threads[NUM_THREADS];
    pthread_mutex_init(&lock, NULL);
    
    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_create(&threads[i], NULL, increment, NULL);
    }
    
    for (int i = 0; i < NUM_THREADS; i++) {
        pthread_join(threads[i], NULL);
    }
    
    printf("Final counter value: %d\n", counter);
    pthread_mutex_destroy(&lock);
    return 0;
}
```

---

## Exercise 3: Page Replacement

**Objective**: Implement LRU page replacement algorithm.

**Task**: Write a program that:
1. Takes a page reference string as input
2. Takes number of frames as parameter
3. Implements LRU page replacement
4. Counts page faults

**Input Format**:
```
Pages: 7 0 1 2 0 3 0 4 2 3 0 3 2 1 2 0 1 7 0 1
Frames: 3
```

**Expected Output**:
```
Page Faults: 12
Hit Rate: 40%
```

**Solution Pattern**:
```python
def lru_page_replacement(pages, num_frames):
    frames = []
    page_faults = 0
    recent_usage = {}
    
    for i, page in enumerate(pages):
        if page not in frames:
            page_faults += 1
            if len(frames) >= num_frames:
                # Find LRU page
                lru_page = min(recent_usage, key=recent_usage.get)
                frames.remove(lru_page)
            frames.append(page)
        recent_usage[page] = i
    
    return page_faults

# Test
pages = [7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1]
faults = lru_page_replacement(pages, 3)
print(f"Page Faults: {faults}")
```

---

## Exercise 4: Deadlock Detection

**Objective**: Implement Banker's Algorithm.

**Task**: Write a program that:
1. Takes current allocation matrix, max matrix, and available resources
2. Determines if system is in safe state
3. Outputs safe sequence if one exists

**Input Format**:
```
Processes: 5
Resources: 3

Allocation:
0 1 0
2 0 0
3 0 2
2 1 1
0 0 2

Max:
7 5 3
3 2 2
9 0 2
2 2 2
4 3 3

Available:
3 3 2
```

**Expected Output**:
```
System is in safe state.
Safe sequence: P1 P3 P4 P0 P2
```

**Solution Pattern**:
```python
def bankers_algorithm(allocation, max_matrix, available):
    n = len(allocation)  # processes
    m = len(available)   # resources
    
    work = available[:]
    finish = [False] * n
    safe_sequence = []
    
    need = [[max_matrix[i][j] - allocation[i][j] 
             for j in range(m)] for i in range(n)]
    
    while len(safe_sequence) < n:
        found = False
        for i in range(n):
            if not finish[i]:
                if all(need[i][j] <= work[j] for j in range(m)):
                    work = [work[j] + allocation[i][j] for j in range(m)]
                    finish[i] = True
                    safe_sequence.append(f'P{i}')
                    found = True
        
        if not found:
            return None, need
    
    return safe_sequence, need
```

---

## Exercise 5: File System Simulation

**Objective**: Simulate inode-based file system.

**Task**: Write a program that:
1. Implements inode structure with direct/indirect pointers
2. Supports file creation, read, write operations
3. Manages free space bitmap
4. Simulates file allocation

**Data Structures**:
```c
#define BLOCK_SIZE 4096
#define MAX_FILE_SIZE (12 * BLOCK_SIZE + BLOCK_SIZE/4 * BLOCK_SIZE)

typedef struct {
    int size;
    int direct[12];
    int indirect;
    int double_indirect;
    char permissions;
    time_t created;
    time_t modified;
} Inode;

typedef struct {
    Inode inodes[1024];
    char free_bitmap[128];  // 1024 bits
} FileSystem;
```

**Expected Output**:
```
Created file: test.txt (inode 1)
Wrote 5000 bytes to test.txt
File allocated to blocks: [5, 6, 7]
Read from test.txt: 5000 bytes
```

---

## Exercise 6: Disk Scheduling

**Objective**: Compare disk scheduling algorithms.

**Task**: Write a program that:
1. Takes disk request queue as input
2. Implements FCFS, SSTF, SCAN, C-SCAN
3. Calculates total head movement for each
4. Compares performance

**Input Format**:
```
Requests: 98 183 37 122 14 124 65 67
Initial head: 53
Direction: right
Disk size: 200
```

**Expected Output**:
```
FCFS: Total movement = 640
SSTF: Total movement = 236
SCAN: Total movement = 382
C-SCAN: Total movement = 382
```

**Solution Pattern**:
```python
def fcfs(requests, head):
    total = 0
    current = head
    for req in requests:
        total += abs(req - current)
        current = req
    return total

def scan(requests, head, disk_size, direction='right'):
    total = 0
    current = head
    sorted_reqs = sorted(requests)
    
    if direction == 'right':
        right = [r for r in sorted_reqs if r >= head]
        left = [r for r in sorted_reqs if r < head][::-1]
        order = right + [disk_size - 1] + left
    else:
        left = [r for r in sorted_reqs if r <= head][::-1]
        right = [r for r in sorted_reqs if r > head]
        order = left + [0] + right
    
    for req in order:
        total += abs(req - current)
        current = req
    return total
```

---

## Exercise 7: Producer-Consumer with Semaphores

**Objective**: Implement bounded buffer problem.

**Task**: Write a C program that:
1. Creates producer and consumer threads
2. Uses semaphores for synchronization
3. Implements bounded buffer (size 5)
4. Producer produces 20 items, consumer consumes all

**Expected Output**:
```
Producer: produced item 0
Consumer: consumed item 0
...
Producer: produced item 19
Consumer: consumed item 19
All items consumed.
```

**Solution Pattern**:
```c
#include <stdio.h>
#include <pthread.h>
#include <semaphore.h>

#define BUFFER_SIZE 5
#define NUM_ITEMS 20

int buffer[BUFFER_SIZE];
int in = 0, out = 0;

sem_t empty, full;
pthread_mutex_t mutex;

void* producer(void* arg) {
    for (int i = 0; i < NUM_ITEMS; i++) {
        sem_wait(&empty);
        pthread_mutex_lock(&mutex);
        
        buffer[in] = i;
        printf("Producer: produced item %d\n", i);
        in = (in + 1) % BUFFER_SIZE;
        
        pthread_mutex_unlock(&mutex);
        sem_post(&full);
    }
    return NULL;
}

void* consumer(void* arg) {
    for (int i = 0; i < NUM_ITEMS; i++) {
        sem_wait(&full);
        pthread_mutex_lock(&mutex);
        
        int item = buffer[out];
        printf("Consumer: consumed item %d\n", item);
        out = (out + 1) % BUFFER_SIZE;
        
        pthread_mutex_unlock(&mutex);
        sem_post(&empty);
    }
    return NULL;
}
```

---

## Exercise 8: Virtual Memory Simulation

**Objective**: Simulate page table and TLB.

**Task**: Write a program that:
1. Simulates page table with N entries
2. Implements TLB with M entries
3. Processes memory references
4. Calculates hit rate and effective access time

**Parameters**:
- Page table access: 100 ns
- TLB access: 10 ns
- Memory access: 100 ns
- TLB size: 16 entries
- Page size: 4 KB

**Expected Output**:
```
TLB Hits: 45
TLB Misses: 55
TLB Hit Rate: 45%
Effective Access Time: 155 ns
```
