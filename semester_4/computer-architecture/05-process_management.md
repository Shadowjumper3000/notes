## Inter-Process Communication (IPC)

Inter-process communication (IPC) allows processes to exchange data and synchronize their execution. IPC mechanisms enable cooperation between processes running on the same machine or different machines over a network.

### Data Exchange Mechanisms

These IPC methods facilitate data sharing between processes:

#### **Pipe**

- Unidirectional communication: Data flows in a single direction from a writer to a reader.
- Two types:
    - **Anonymous Pipes**: Used between a parent and child process or between processes that share a common ancestor.
    - **Named Pipes (FIFOs)**: Not limited to parent-child relationships, allowing communication between unrelated processes.

#### **Signals**

- Lightweight messaging system used to notify a process about an event.
- Examples include:
    - `SIGINT` (interrupt)
    - `SIGKILL` (force termination)
    - `SIGSTOP` (pause execution)
- Processes can handle or ignore certain signals, except for `SIGKILL` and `SIGSTOP`.

#### **Message Queues**

- Allow processes to send structured messages to each other.
- Messages can include real information, unlike signals.
- Persist beyond process termination, unlike pipes.
- Used in applications requiring prioritized messaging, such as inter-service communication.

#### **Shared Memory**

- Enables multiple processes to access the same section of physical memory.
- Fastest IPC mechanism since no data copying is required.
- Requires synchronization mechanisms (e.g., mutexes) to prevent race conditions.

#### **Memory-Mapped Files**

- Maps files or device memory into a process’s address space.
- Multiple processes can access the same mapped file concurrently.
- Useful for large datasets and file-based IPC.

#### **Sockets**

- Provide two-way communication over a network.
- Supports both local (UNIX domain sockets) and remote (TCP/IP, UDP) communication.
- Can be used for client-server architectures and distributed systems.

---

## Process Synchronization

Process synchronization is necessary to prevent race conditions and ensure the correctness of concurrent operations. Key synchronization mechanisms include:

### **Critical Section Problem**

- Occurs when multiple processes try to access a shared resource concurrently.
- Must be resolved to prevent data inconsistencies.

### **Mutex (Mutual Exclusion Object)**

- Ensures only one process can access a shared resource at a time.
- Used to prevent race conditions in critical sections.

### **Monitors**

- Higher-level synchronization construct that combines mutual exclusion and condition variables.
- Encapsulates shared resources and ensures only one process accesses them at a time.

### **Semaphore**

- A counter used to manage access to shared resources.
- Two types:
    - **Binary Semaphore** (acts like a mutex, allowing only one process at a time)
    - **Counting Semaphore** (allows a limited number of processes to access a resource concurrently)
- Operations:
    - `wait()` (decrements the semaphore, blocking if necessary)
    - `signal()` (increments the semaphore, waking up waiting processes if any)
- Used in producer-consumer problems, resource allocation, and multi-threading scenarios.

### **Deadlocks**

A deadlock occurs when two or more processes are waiting indefinitely for resources held by each other. Four necessary conditions for deadlocks:

1. **Mutual Exclusion**: Only one process can use a resource at a time.
2. **Hold and Wait**: A process holding at least one resource is waiting to acquire additional resources held by other processes.
3. **No Preemption**: A resource cannot be forcibly taken away from a process; it must be released voluntarily.
4. **Circular Wait**: A set of processes form a circular chain, each waiting for a resource held by the next process in the chain.

To handle deadlocks, various strategies can be used:

- **Deadlock Prevention**: Eliminating one of the necessary conditions.
- **Deadlock Avoidance**: Using algorithms like the Banker’s Algorithm to ensure the system remains in a safe state.
- **Deadlock Detection and Recovery**: Detecting deadlocks and taking actions such as process termination or resource preemption to recover from them.

These IPC and synchronization mechanisms help ensure smooth communication and resource management in multi-process applications.