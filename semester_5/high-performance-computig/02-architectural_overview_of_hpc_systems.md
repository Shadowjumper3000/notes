# High-Performance Computing (HPC) Cluster Components

## Cluster Components

### Login Nodes
- Handle user connections to the cluster.
- Should **not** be used for computations.
- Intended primarily for:
  - Compiling code
  - Submitting jobs
  - File management and preparation

### Shared Filesystem
- Centralized storage accessible by all nodes.
- Optimized for high-speed I/O operations to support cluster workloads.
- Examples include Lustre, GPFS, or NFS.

### Compute Nodes
- Execute jobs submitted to the cluster.
- Typical components:
  - **CPU(s)** – central processing units for computation.
  - **RAM** – volatile system memory for active tasks.
  - **Local storage** – HDD or SSD for temporary storage.
  - **GPU(s)** – for parallel computing and acceleration.
- Nodes are interconnected using high-speed networking to facilitate communication and data transfer.

### Node Components
- **CPU** – executes program instructions.
- **RAM** – temporary storage for active data and instructions.
- **HDD/SSD** – local persistent storage.
- **GPU** – accelerates parallel workloads.
- **NIC (Network Interface Card)** – facilitates inter-node communication.

---

## Networks in HPC
- **Fat Tree** – hierarchical network with balanced bandwidth across all nodes.
- **Dragonfly** – low-diameter network topology optimized for scalability.
- Other interconnect topologies may be used depending on system design and workload requirements.

---

## Flynn’s Taxonomy (Parallel Architectures)
- **SISD** – Single Instruction, Single Data: traditional serial execution.
- **SIMD** – Single Instruction, Multiple Data: vectorized operations, GPU threads.
- **MISD** – Multiple Instruction, Single Data: rare, mainly in fault-tolerant systems.
- **MIMD** – Multiple Instruction, Multiple Data: clusters, multicore CPUs, multi-threaded systems.

---

## Memory Technology

- **NVRAM** – non-volatile memory, retains data without power.
- **DRAM** – main memory with moderate latency (~100–200 cycles).
- **SRAM** – fast memory, used in caches.

### Cache Hierarchy
- **L1 Cache** – inside the core, extremely fast (few cycles per access).
- **L2 Cache** – per-core or shared, slightly slower (4–20 cycles).
- **DRAM** – slower main memory (100–200 cycles).

---

## CPU Architecture

### Components
- **Cores** – each core has a control unit and arithmetic logic unit (ALU).
- **Registers + L1 Cache** – fastest memory inside each core.
- **L2 Cache** – per-core or shared across cores.
- **DDR Memory (DIMMs)** – main memory connected to the compute board.
- **I/O Subsystem** – interfaces for networking, PCIe, storage, and peripherals.

### Modern CPU Features
- Combines high-performance and energy-efficient cores.
- Distributed L2 and L3 caches for optimized parallel access.
- **Ring agent** for inter-core communication.
- Integrated GPUs and media engines for AI or visualization.
- High-speed memory and I/O interfaces.

### Core Types
- **Golden Cove** – high-performance cores for intensive workloads.
- **Gracemont** – energy-efficient cores for lighter tasks.

### Specialized Units
- **FPU / SIMD** – floating-point and vector operations.
- **TMUs (Texture Mapping Units)** – GPU graphics operations.
- **Media Engines** – video encoding and decoding.
- **PCIe / DM4.0 Lanes** – high-speed external connectivity.

---

## Instruction Set Architecture (ISA)
- Defines the “grammar” of machine language.

### CISC (Complex Instruction Set Computing)
- Fewer instructions per program, each instruction may require multiple cycles.
- Optimized to reduce code size.

### RISC (Reduced Instruction Set Computing)
- Simplified instructions, minimal cycles per instruction.
- Requires more instructions to complete the same task.

---

## CPU vs Accelerators

### CPU
**Strengths:**
- High single-thread performance (out-of-order execution, high clock speed).
- Handles poorly parallelized applications efficiently.
- Large memory per core.
- Supports standard HPC environments (MPI, OpenMP).
- Autonomous operation.

**Weaknesses:**
- High power consumption.
- Higher cost per performance unit.

### Accelerators (GPU, etc.)
**Strengths:**
- High throughput and FLOP/Watt efficiency.
- Optimized for massively parallel workloads.
- High memory bandwidth.

**Weaknesses:**
- Low single-thread performance.
- Requires specialized programming (CUDA, HIP, OpenCL).
- Dependent on host CPU.
- Limited onboard memory.

### CPU vs GPU Summary
- **CPU**: optimized for low latency, flexible workloads, large caches.  
- **GPU**: optimized for high throughput, parallel execution, energy efficiency.

---

## Managing HPC Resources

- HPC clusters allocate resources to user jobs via a **resource manager and scheduler**.
- Jobs: self-contained units with input data → execution → output results.
- Jobs can be **interactive** (real-time execution) or **batch** (queued execution).

### Core Functions
1. **Job Scheduling**
   - Determines order and placement of computational tasks.
   - Algorithms: FIFO, backfilling, gang scheduling, preemption.
2. **Resource Allocation**
   - **Static**: fixed resources for job duration.
   - **Dynamic**: resources adjust to current load and requirements.
3. **Load Balancing**
   - Ensures even workload distribution.
   - Algorithms: Round Robin, Least Connections, Weighted Distribution.
4. **Monitoring and Reporting**
   - Tracks usage, progress, and system health.
5. **Job Prioritization**
   - Assigns priority levels to manage critical workloads.
6. **User Management and Accounting**
   - Tracks resource usage, enforces permissions, ensures fair allocation.
7. **Fault Tolerance**
   - Checkpointing and recovery strategies to minimize job impact from failures.

### Resource Types
- **GRES (Generic Resources):** accelerators, special devices.
- **TRES (Trackable Resources):** CPUs, memory, energy, licenses.

---

## SLURM Overview

- SLURM manages **compute nodes** via **partitions** (job queues).
- **Scheduler** assigns available nodes to the highest-priority eligible jobs.
- Jobs can use all nodes or a subset; supports **job arrays**.
- **Scheduling Concepts:**
  - Event-triggered: schedule upon job submission, completion, or config change.
  - Backfill scheduling: starts smaller jobs ahead of larger ones for efficiency.
  - Gang scheduling: synchronizes jobs with similar characteristics.
  - Preemption: interrupts lower-priority jobs to run high-priority ones.
- **Elastic Computing:** dynamically resize job resources; can extend cluster to cloud.
- **High-Throughput Computing:** supports large numbers of small, loosely coupled jobs.

### SLURM Commands Example
```bash
srun -N 4 -n 8 ./programr

Job Submission
- Submit batch job:
  sbatch job_script.sh
- Submit interactive job:
  srun --pty bash

Job Status
- Show all jobs:
  squeue
- Show jobs for a specific user:
  squeue -u username
- Show detailed job info:
  scontrol show job <job_id>

Job Management
- Cancel a job:
  scancel <job_id>
- Hold a job:
  scontrol hold <job_id>
- Release a held job:
  scontrol release <job_id>

Resource Requests
- Request nodes and tasks:
  srun -N <nodes> -n <tasks> ./program
- Request memory per CPU:
  sbatch --mem-per-cpu=4G job_script.sh
- Request GPU:
  sbatch --gres=gpu:1 job_script.sh

Job Arrays
- Submit array jobs:
  sbatch --array=1-10 job_script.sh
- Access array index in script:
  echo $SLURM_ARRAY_TASK_ID

Job Output
- Redirect output and error:
  sbatch -o output.log -e error.log job_script.sh

Partitions
- List partitions:
  sinfo
- Submit to specific partition:
  sbatch -p partition_name job_script.sh

Advanced
- Job dependencies:
  sbatch --dependency=afterok:<job_id> job_script.sh
- Limit job runtime:
  sbatch -t HH:MM:SS job_script.sh
