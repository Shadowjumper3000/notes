# High-Performance Computing

## Table of Contents

[[01-fundamentals_of_hpc|Fundamentals of HPC]]
[[02-architectural_overview_of_hpc_systems|Architectural Overview of HPC Systems]]
[[03-memory_management|Memory Management]]
[[04-benchmarks|Benchmarks]]
[[05-virtualization|Virtualization]]
[[06-midterm_prep|Midterm Prep]]

## Course Overview

This course explores the architecture, programming, and optimization of high-performance computing (HPC) systems. Topics include parallel architectures, memory hierarchies, performance benchmarking, and distributed computing.

---

## Table of Contents

### Core Topics

1. [[Fundamentals of HPC|HPC Fundamentals]]
   - Parallel computing concepts
   - Performance metrics (FLOPS, bandwidth)
   - Scalability and efficiency
   - Amdahl's Law and Gustafson's Law
   - HPC applications

2. [[Architectural overview of HPC systems|HPC System Architecture]]
   - Cluster components (login nodes, compute nodes)
   - Shared filesystems
   - Network interconnects
   - Flynn's taxonomy (SISD, SIMD, MIMD)
   - Memory hierarchy and cache
   - CPU vs accelerators (GPUs, FPGAs)
   - Instruction set architectures (CISC vs RISC)

3. [[MemoryManagement|Parallel Programming]]
   - OpenMP (shared memory)
   - MPI (distributed memory)
   - Thread management
   - Synchronization primitives
   - Race conditions and deadlocks
   - Load balancing

4. [[Benchmarks|Performance Benchmarks]]
   - LINPACK (HPL)
   - HPCG (High-Performance Conjugate Gradient)
   - STREAM (memory bandwidth)
   - IO500 (storage performance)
   - SPEC benchmarks
   - Graph500, Green500
   - MLPerf (machine learning)

5. [[Virtualization|Virtualization Technologies]]
   - Hypervisors and virtual machines
   - Container technologies
   - Resource isolation
   - Performance overhead
   - Use cases in HPC

6. [[Midterm Prep|Exam Preparation]]

---

## Key Concepts

### Parallel Computing
- **Shared memory**: Multiple threads, single address space
- **Distributed memory**: Multiple processes, message passing
- **Hybrid models**: Combining shared and distributed
- **Data parallelism**: Same operation on different data
- **Task parallelism**: Different operations concurrently

### Performance Optimization
- **Cache optimization**: Locality of reference
- **Vectorization**: SIMD instructions
- **Load balancing**: Distributing work evenly
- **Communication minimization**: Reducing overhead
- **I/O optimization**: Parallel filesystems

### Architecture
- **Supercomputers**: Massively parallel systems
- **Clusters**: Commodity hardware interconnected
- **Accelerators**: GPUs for compute-intensive tasks
- **Networks**: InfiniBand, Ethernet for low latency

---

## Programming Models

### OpenMP
```c
#pragma omp parallel for
for (int i = 0; i < n; i++) {
    // Parallel loop body
}
```

### MPI
```c
MPI_Send(buffer, count, datatype, dest, tag, comm);
MPI_Recv(buffer, count, datatype, source, tag, comm, &status);
```

### CUDA (GPU Programming)
```cuda
__global__ void kernel(float *data, int n) {
    int idx = blockIdx.x * blockDim.x + threadIdx.x;
    // GPU computation
}
```

---

## Applications

- Weather forecasting and climate modeling
- Molecular dynamics simulations
- Computational fluid dynamics
- Finite element analysis
- Machine learning training
- Genomics and bioinformatics
- Cryptography and security
- Financial modeling

---

## Prerequisites

- Computer architecture fundamentals
- C/C++ or Fortran programming
- Operating systems concepts
- Linear algebra basics

---

## Learning Objectives

By the end of this course, you should be able to:
1. Understand parallel computing architectures
2. Write parallel programs using OpenMP and MPI
3. Optimize code for cache and memory hierarchy
4. Benchmark and profile HPC applications
5. Analyze scalability and performance
6. Use HPC resources effectively
7. Debug parallel programs
8. Apply HPC techniques to scientific problems

---

## Performance Metrics

### Key Measurements
- **FLOPS**: Floating-point operations per second
- **Bandwidth**: Data transfer rate
- **Latency**: Time delay for operations
- **Scalability**: Performance vs number of processors
- **Efficiency**: Actual speedup / ideal speedup
- **Power consumption**: Energy per computation

### Benchmarks Overview

| Benchmark | Focus Area | Key Metric |
|-----------|------------|------------|
| LINPACK | Dense linear algebra | FLOPS |
| HPCG | Sparse iterative methods | GFLOPS |
| STREAM | Memory bandwidth | GB/s |
| IO500 | Storage I/O | IOPS, bandwidth |
| Graph500 | Graph analytics | GTEPS |
| Green500 | Energy efficiency | FLOPS/Watt |

---

## Further Topics

- Advanced MPI features (non-blocking, collective operations)
- GPU programming (CUDA, OpenCL, OpenACC)
- Performance analysis tools (profilers, debuggers)
- Parallel algorithms and data structures
- Fault tolerance in large-scale systems
- Quantum computing introduction
