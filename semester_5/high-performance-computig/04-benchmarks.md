# HPC Performance Benchmarks

High-Performance Computing (HPC) systems are evaluated using different benchmarks, each targeting a specific aspect of performance. No single benchmark captures all bottlenecks, so multiple are used in practice.

---

## 1. LINPACK (HPL)
- **Measures:** Floating-point performance by solving dense systems of linear equations.  
- **Use Case:** Basis of the **TOP500 list**.  
- **Strengths:** Highlights raw compute (FLOPS).  
- **Limitations:** Optimistic; favors dense math, not memory- or communication-heavy workloads.  

---

## 2. HPCG (High-Performance Conjugate Gradient)
- **Measures:** Sparse linear algebra, memory bandwidth, and communication.  
- **Use Case:** More realistic for scientific and engineering applications.  
- **Strengths:** Tests compute + memory + network.  
- **Limitations:** Yields lower FLOPS than LINPACK, harder to optimize.  

---

## 3. STREAM
- **Measures:** Sustainable memory bandwidth.  
- **Use Case:** Memory-bound workloads (e.g., CFD, finite elements).  
- **Strengths:** Simple and widely adopted.  
- **Limitations:** Narrow focus; ignores compute and communication.  

---

## 4. IO500
- **Measures:** I/O performance of parallel filesystems (throughput + metadata ops).  
- **Use Case:** Checkpoint/restart, data-intensive workloads.  
- **Strengths:** Realistic stress test for HPC storage.  
- **Limitations:** Does not evaluate compute or networking.  

---

## 5. SPEC MPI / SPEC OMP
- **Measures:** Application-level performance using standardized workloads:  
  - **SPEC MPI** → distributed-memory (MPI).  
  - **SPEC OMP** → shared-memory (OpenMP).  
- **Use Case:** Proxy for end-user applications.  
- **Strengths:** Application realism.  
- **Limitations:** Complex, no single summary metric.  

---

## 6. Graph500
- **Measures:** Graph analytics performance (e.g., BFS, shortest paths).  
- **Use Case:** Non-numerical workloads (bioinformatics, security, AI).  
- **Strengths:** Targets irregular, data-intensive computation.  
- **Limitations:** Niche; not directly comparable with LINPACK/HPCG.  

---

## 7. Green500
- **Measures:** Energy efficiency (FLOPS per watt, based on LINPACK).  
- **Use Case:** Power-aware HPC design.  
- **Strengths:** Highlights energy-efficient architectures.  
- **Limitations:** Biased toward LINPACK-style workloads.  

---
## 8. DeepBench

- **Measures:** Performance of deep learning primitives (matrix multiply, convolution, recurrent ops, communication).
- **Use Case:** Benchmarking HPC systems and accelerators for AI workloads.
- **Strengths:** Low-level kernels → insight into hardware suitability for DL training.
- **Limitations:** Microbenchmarks only; doesn’t reflect full application performance.
---

## 9. MLPerf

- **Measures:** End-to-end ML training and inference performance across diverse models (vision, NLP, recommendation, reinforcement learning).
- **Use Case:** Industry-standard AI benchmark.
- **Strengths:** Application-level, broad workload coverage, compares hardware/software stacks.
- **Limitations:** Complex setup, results influenced by framework optimizations.

---

## 📊 Summary Mapping (Extended)

|Benchmark|Focus Area|Strengths|Limitations|
|---|---|---|---|
|LINPACK|Peak compute (FLOPS)|Basis of TOP500|Unrealistic for many workloads|
|HPCG|Sparse compute + comm|More realistic|Lower FLOPS, harder to optimize|
|STREAM|Memory bandwidth|Simple, useful for memory|Narrow focus|
|IO500|Storage I/O|Filesystem stress test|No compute/network insight|
|SPEC MPI/OMP|Application realism|Proxy for real workloads|Complex, no single number|
|Graph500|Graph/data analytics|Non-numerical workloads|Niche relevance|
|Green500|Energy efficiency|Highlights power efficiency|Biased to LINPACK|
|DeepBench|DL primitives (kernels)|Hardware suitability for DL|Microbenchmarks only|
|MLPerf|End-to-end ML workloads|Broad, standardized, realistic|Complex, framework-dependent|
