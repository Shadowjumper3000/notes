# Random Access Memory (RAM)

**Tags:** #concept #cs #hardware #architecture
**Related:** [[Arrays]], [[Matrices and Linear Maps]]

## Definition

**Random Access Memory (RAM)** is the primary form of volatile memory in a computer system. It provides fast read/write access to data that the CPU is actively using. "Random access" means any memory location can be accessed directly in constant time, regardless of its physical position — as opposed to sequential access in tape or disk storage.

## Memory Hierarchy

RAM sits in a specific position in the memory hierarchy, between fast-but-small cache and slow-but-large storage:

| Level | Technology | Size | Latency (approx.) | Bandwidth |
|---|---|---|---|---|
| **Register** | Flip-flops | ~1 KB | 0.3 ns | 1000+ GB/s |
| **L1 Cache** | SRAM | ~32 KB | 0.5-1 ns | 500 GB/s |
| **L2 Cache** | SRAM | ~256 KB | 3-5 ns | 200 GB/s |
| **L3 Cache** | SRAM | ~8 MB | 10-20 ns | 100 GB/s |
| **RAM** | DRAM | 4-64 GB | 50-100 ns | 20-50 GB/s |
| **SSD** | Flash | 256 GB-4 TB | 10-100 $\mu$s | 1-5 GB/s |
| **HDD** | Magnetic | 1-20 TB | 5-15 ms | 100-200 MB/s |

The key observation is the **latency gap**: RAM is about 100$\times$ slower than L1 cache and about 1000$\times$ faster than disk. This gap motivates caching strategies and data locality optimizations.

## Cell Structure

### SRAM (Static RAM)
- Uses a bistable flip-flop (typically 6 transistors per bit)
- Data persists as long as power is applied
- Faster but less dense than DRAM
- Used for CPU caches

### DRAM (Dynamic RAM)
- Uses a single transistor + capacitor per bit
- Capacitor charge represents the bit value; it leaks over time (milliseconds)
- Requires periodic **refresh** (typically every 64 ms)
- Much denser than SRAM (higher capacity per chip)
- Used for main memory

### DRAM Cell Operation

A DRAM cell stores charge $Q = C \cdot V$ on a capacitor. Reading involves:

$$
V_{\text{out}} = V_{\text{ref}} \pm \Delta V, \quad \Delta V \approx \frac{C_{\text{cell}}}{C_{\text{bitline}}} \cdot \frac{V_{\text{dd}}}{2}
$$

The read is destructive — the cell must be recharged after reading. Modern DDR (Double Data Rate) SDRAM transfers data on both rising and falling clock edges.

## Addressing

Memory is organized as a linear array of $N$ addressable units (typically bytes). An address is an integer $a \in \{0, 1, \dots, N-1\}$. With $n$-bit addresses, the maximum addressable memory is:

$$
\text{Max memory} = 2^n \text{ bytes}
$$

For $n = 64$: $2^{64}$ bytes = 16 exabytes.

### Address Decoding

Internally, DRAM is organized as a **grid** (rows $\times$ columns). A memory address is split into row and column components:

$$
\text{Address} = \text{Row Address} \times 2^{\text{column bits}} + \text{Column Address}
$$

This is the **bit matrix** structure. For a $32 \times 32$ bit matrix, the address $\text{0xAB}$ decodes as:

$$
\text{Row} = \lfloor \text{0xAB} / 32 \rfloor = 5, \quad \text{Column} = \text{0xAB} \bmod 32 = 11
$$

### Row Buffer Locality

When a DRAM row is accessed, the entire row is loaded into a **row buffer** (typically 1-8 KB). Accessing a different column in the same row is much faster (column access strobe, CAS latency) than accessing a different row (which requires precharge + row access strobe, tRP + tRCD).

This is why **spatial locality** matters: sequential access to adjacent memory addresses hits the same DRAM row.

## Latency vs Capacity Tradeoffs

The relationship between memory capacity and latency is governed by fundamental physical constraints:

- **RC delay:** Wire delay scales as $RC \propto L^2$, where $L$ is wire length. Larger memories have longer wires, increasing latency.
- **Density vs speed:** DRAM cells are optimized for density (small capacitor, single transistor), which makes them slower than SRAM.
- **Bandwidth scaling:** DDR generations improve bandwidth faster than latency:

| Generation | Peak Transfer Rate | CAS Latency |
|---|---|---|
| DDR3-1600 | 12.8 GB/s | 11 cycles (13.75 ns) |
| DDR4-3200 | 25.6 GB/s | 16 cycles (10 ns) |
| DDR5-6400 | 51.2 GB/s | 22 cycles (6.875 ns) |

Absolute latency improves modestly, while bandwidth doubles per generation.

### Memory Wall

The **memory wall** refers to the growing disparity between CPU speed (doubling ~every 2 years historically) and memory latency (improving ~7% per year). This motivates:

1. Multi-level caches
2. Prefetching hardware
3. Out-of-order execution
4. Simultaneous multithreading (hiding latency)

## Relation to Data Structures

The physical characteristics of RAM directly influence data structure design:

### Arrays (Contiguous Allocation)

An array of $n$ elements of size $s$ bytes occupies a contiguous block of $n \cdot s$ bytes:

$$
\text{address}(\text{arr}[i]) = \text{base} + i \cdot s
$$

Access is $O(1)$. Iterating sequentially exploits spatial locality and DRAM row buffers.

### Matrices and Memory Layout

For a matrix $A \in \mathbb{R}^{m \times n}$, the layout matters:

- **Row-major** (C, Python): $A[i][j] = \text{base} + i \cdot n \cdot s + j \cdot s$
- **Column-major** (Fortran, MATLAB): $A[i][j] = \text{base} + j \cdot m \cdot s + i \cdot s$

Choosing the wrong layout causes cache misses. A matrix-vector multiply $A\mathbf{x}$ should iterate in storage order to maximize cache utilization:

$$
y_i = \sum_{j} A_{ij} x_j
$$

In row-major, the inner loop over $j$ accesses consecutive memory locations.

### Cache-Oblivious Algorithms

Cache-oblivious algorithms are designed to work well at all levels of the memory hierarchy without knowing cache parameters. For matrix multiplication, a blocked (tiled) approach:

$$
C = C + A \cdot B
$$

Using a block size $B$ that fits in cache:

$$
C_{ij} = C_{ij} + \sum_{k=1}^{n/B} A_{i, k} B_{k, j}
$$

This reduces cache misses from $O(n^3)$ to $O(n^3 / \sqrt{M})$ where $M$ is cache size.

### Page Tables and Virtual Memory

Modern operating systems use **virtual memory** with page tables. A virtual address is split:

$$
\text{Virtual Address} = \underbrace{\text{Page Number}}_{\text{virtual page}} + \underbrace{\text{Offset}}_{\text{in-page}}
$$

The TLB (Translation Lookaside Buffer) caches recent page table entries. A TLB miss incurs a RAM access to traverse the page table — a key performance consideration for large working sets.

## Relationships to Other Notes

- [[Arrays]]: Arrays map directly to contiguous RAM; $O(1)$ indexing relies on constant-time random access.
- [[Matrices and Linear Maps]]: Matrix storage layout (row/column-major) determines cache efficiency; the performance of $A\mathbf{x}$ depends on memory access patterns.
- [[Vectors and Vector Spaces]]: Vector operations like the dot product $\langle \mathbf{u}, \mathbf{v} \rangle = \sum u_i v_i$ require sequential memory access for good performance.

## References

- Hennessy, J. L., & Patterson, D. A. (2019). *Computer Architecture: A Quantitative Approach*. Morgan Kaufmann.
- Jacob, B., Ng, S., & Wang, D. (2007). *Memory Systems: Cache, DRAM, Disk*. Morgan Kaufmann.
- Drepper, U. (2007). "What Every Programmer Should Know About Memory." Red Hat.
