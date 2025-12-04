# Queueing Discipline in Probability for Computing

## 1. Introduction
- **Queueing Discipline**: Rules determining the order of service for entities (e.g., packets, processes) in a queue.
- **Key Applications**: 
  - Network packet scheduling (routers, switches).
  - CPU task scheduling (OS).
  - Call center management.

## 2. Common Queueing Disciplines

| Discipline          | Description                                                                 | Pros & Cons                                                                 |
|---------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| **FIFO** (First-In-First-Out) | Serves entities in arrival order.                                         | ✅ Simple, fair. ❌ No priority handling, poor for time-sensitive traffic.    |
| **LIFO** (Last-In-First-Out)  | Serves the most recent arrival first.                                      | ✅ Useful for stack-like systems. ❌ May starve older requests.              |
| **Priority Queueing**          | Entities grouped by priority; higher priority served first.                | ✅ Critical tasks handled first. ❌ Starvation of low-priority queues.        |
| **Round Robin (RR)**           | Cycles through queues, serving a fixed time slice per queue.               | ✅ Fairness, no starvation. ❌ Overhead from context switching.              |
| **Weighted Fair Queueing (WFQ)** | Allocates bandwidth proportionally to weights.                            | ✅ Balances fairness and priority. ❌ Complex to implement.                  |
| **Shortest Job First (SJF)**   | Serves the entity with the smallest processing time next.                  | ✅ Minimizes average waiting time. ❌ Requires knowledge of job lengths.      |
| **Shortest Remaining Time (SRT)** | Preemptive version of SJF.                                              | ✅ Better than SJF for dynamic systems. ❌ High overhead.                     |

## 3. Key Metrics for Evaluation
- **Average Waiting Time**: Mean time an entity spends in the queue.
- **Throughput**: Number of entities processed per unit time.
- **Queue Length**: Number of entities waiting at a given time.
- **Starvation**: Low-priority entities never get served.

## 4. Mathematical Foundations
### 4.1. Kendall's Notation (`A/B/C/D/E`)
Describes queueing systems using 5 components:
1. **A**: Arrival process (e.g., `M` for Markovian/Poisson).
2. **B**: Service time distribution (e.g., `M` for exponential, `D` for deterministic).
3. **C**: Number of servers (e.g., `1`, `n`).
4. **D**: System capacity (e.g., `∞` for unlimited).
5. **E**: Queueing discipline (e.g., `FIFO`, `PS` for processor sharing).

**Example**:  
`M/M/1/FIFO` = Poisson arrivals, exponential service times, single server, FIFO discipline.

### 4.2. Little's Law
Relates steady-state metrics:  
\( L = \lambda W \)  
- \( L \): Average number of entities in the system.
- \( \lambda \): Arrival rate.
- \( W \): Average time an entity spends in the system.

## 5. Case Study: Network Packet Scheduling
- **FIFO**: Default in most routers (simple but unfair under congestion).
- **Weighted Fair Queueing (WFQ)**: Used in QoS to prioritize VoIP over file downloads.
- **Random Early Detection (RED)**: Drops packets probabilistically to prevent congestion.

## 6. Advanced Topics
- **Processor Sharing (PS)**: All jobs share server resources equally (idealized CPU model).
- **Multilevel Queueing**: Combines multiple disciplines (e.g., OS scheduling with foreground/background tasks).
- **Preemptive vs. Non-Preemptive**:  
  - Preemptive: High-priority entities can interrupt service.  
  - Non-preemptive: Service completes once started.

## 7. Practical Considerations
1. **Overhead**: Complex disciplines (e.g., WFQ) require more computation.
2. **Starvation Mitigation**: Techniques like aging (gradually increasing priority of waiting entities).
3. **Burden of Prediction**: SJF/SRT require estimating service times.

## 8. References
- Kleinrock, L. *Queueing Systems, Volume 1: Theory* (1975).
- Harchol-Balter, M. *Performance Modeling and Design of Computer Systems* (2013).
- RFC 7567 (Network Queueing Discipline Guidelines).