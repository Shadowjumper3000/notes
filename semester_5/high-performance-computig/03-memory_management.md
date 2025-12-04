# Parallel Programming Notes: OpenMP & MPI

## 1. OpenMP (Open Multi-Processing)

OpenMP is an API for shared-memory parallel programming in C, C++, and Fortran.

### 1.1 Basics
- Uses compiler directives (`#pragma`) to specify parallel regions.
- Threads share the same memory space.
- Typical directives:
  - `#pragma omp parallel` → defines a parallel region.
  - `#pragma omp for` → distributes loop iterations across threads.
- Environment variables:
  - `OMP_NUM_THREADS` → sets number of threads.

```c
#include <omp.h>
#include <stdio.h>

int main() {
    #pragma omp parallel
    {
        printf("Hello from thread %d\n", omp_get_thread_num());
    }
    return 0;
}
```
1.2 Synchronization
Locks

    Explicitly control access to critical sections.
```c
omp_lock_t lock;
omp_init_lock(&lock);

omp_set_lock(&lock);
// critical section
omp_unset_lock(&lock);

omp_destroy_lock(&lock);
```
Atomic

    Ensures a single memory update is atomic.
```c
#pragma omp atomic
x += 1;
```
Critical

    Ensures only one thread executes a block at a time.
```c
#pragma omp critical
{
    // code executed by one thread at a time
}
```
1.3 Reductions

    Combine results from threads into a single value.
```c
int sum = 0;
#pragma omp parallel for reduction(+:sum)
for(int i=0; i<N; i++) {
    sum += arr[i];
}
```
    Supported operators: + - * & | ^ && || max min.

2. MPI (Message Passing Interface)

MPI is used for distributed-memory parallel programming.
2.1 Basics

    Each process has its own memory.

    Communicate via message passing.

    Initialize/finalize MPI:
```c
#include <mpi.h>

MPI_Init(NULL, NULL);
MPI_Finalize();

    Each process can query:

        MPI_Comm_rank → process ID (rank)

        MPI_Comm_size → total number of processes
```
2.2 Communication
Point-to-Point
```c
MPI_Send(&data, count, MPI_INT, dest, tag, MPI_COMM_WORLD);
MPI_Recv(&data, count, MPI_INT, source, tag, MPI_COMM_WORLD, &status);
```
Collective Communication

    Broadcast

        Sends data from one process (root) to all processes.
```c
MPI_Bcast(&data, count, MPI_INT, root, MPI_COMM_WORLD);
```
    Scatter

        Divides data among processes.
```c
MPI_Scatter(sendbuf, sendcount, MPI_INT, recvbuf, recvcount, MPI_INT, root, MPI_COMM_WORLD);
```
    Gather

        Collects data from all processes to the root.
```c
MPI_Gather(sendbuf, sendcount, MPI_INT, recvbuf, recvcount, MPI_INT, root, MPI_COMM_WORLD);
```
    Reduction

        Combines data across processes using an operation.
```c
MPI_Reduce(&send, &recv, count, MPI_INT, MPI_SUM, root, MPI_COMM_WORLD);
```
    Common operations: MPI_SUM, MPI_MAX, MPI_MIN, MPI_PROD, MPI_LAND, MPI_LOR.

2.3 Basic Operations

    MPI_Barrier(MPI_COMM_WORLD) → synchronizes all processes.

    Non-blocking: MPI_Isend, MPI_Irecv for asynchronous communication.

    Status: MPI_Status status gives info on received messages.

3. OpenMP vs MPI
Feature	OpenMP	MPI
Memory model	Shared	Distributed
Parallelism	Threads	Processes
Synchronization	Locks, atomic, critical	Message passing
Scope	Single node	Multi-node
Ease of use	Easier	More explicit
4. Summary of Key Directives & Functions
OpenMP

    #pragma omp parallel → parallel region

    #pragma omp for → distribute loop

    #pragma omp critical → mutual exclusion

    #pragma omp atomic → atomic operation

    reduction(op:var) → reduction across threads

MPI

    MPI_Init, MPI_Finalize → setup/teardown

    MPI_Comm_rank, MPI_Comm_size → rank/size

    MPI_Send, MPI_Recv → point-to-point

    MPI_Bcast → broadcast

    MPI_Scatter → distribute chunks

    MPI_Gather → collect chunks

    MPI_Reduce → reductions

    MPI_Barrier → synchronization