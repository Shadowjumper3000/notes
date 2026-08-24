# Greedy Algorithms

A greedy algorithm is an algorithmic paradigm that follows the problem-solving heuristic of making the locally optimal choice at each stage with the intent of finding a global optimum.

## Overview

Greedy algorithms build a solution piece by piece, always choosing the next piece that offers the most immediate benefit. They are typically easy to design and implement but do not always yield the globally optimal solution. A problem must exhibit **optimal substructure** and the **greedy choice property** for a greedy algorithm to be correct.

## Key Properties

- **Greedy choice property**: a globally optimal solution can be arrived at by making a locally optimal (greedy) choice.
- **Optimal substructure**: an optimal solution to the problem contains optimal solutions to its subproblems.
- Greedy algorithms do **not** reconsider choices once made.

## Common Examples

### Activity Selection
Choose the maximum number of non-overlapping activities by selecting the one that finishes earliest.

### Huffman Coding
Build an optimal prefix code by repeatedly merging the two least frequent symbols.

### [[Dijkstra's Algorithm]]
Computes shortest paths by always expanding the nearest unvisited node.

### Fractional Knapsack
Fill a knapsack with items to maximize value; greedy by value-per-weight works optimally because fractions of items can be taken.

## Complexity

Complexity varies widely by problem:
- Sorting-based greedy: $$O(n \log n)$$
- Heap-based greedy: $$O(n \log n)$$
- Linear selection: $$O(n)$$ in some cases.

## When Greedy Works

Greedy algorithms are optimal for:
- [[Minimum Spanning Tree]] (Kruskal's, Prim's algorithms).
- Shortest paths in non-negative graphs ([[Dijkstra's Algorithm]]).
- [[Huffman Coding]].
- Coin change (canonical coin systems).
- Task scheduling with deadlines.

## When Greedy Fails

Classic problems where greedy does **not** yield the global optimum:
- **0/1 Knapsack** — the fractional version works greedily, but the 0/1 version requires [[Dynamic Programming]].
- **Traveling Salesman Problem** — no known greedy selection rule produces an optimal tour.
- **Graph coloring** — greedy coloring may use far more colors than necessary.
- **Coin change** — some coin systems (e.g., US: 1, 10, 25) work greedily, but arbitrary systems do not.

## Applications

- **Data compression** (Huffman coding).
- **Network routing** (Dijkstra, Prim, Kruskal).
- **Scheduling** (job sequencing, interval scheduling).
- **Resource allocation** (cache eviction policies like LRU are greedy).
- **Clustering** (single-linkage clustering).

## Variants

- **Strict greedy**: never revisits a decision (standard model).
- **Adaptive greedy**: may adjust future decisions based on past ones (still one-pass).
- **Randomized greedy**: introduces randomness into the selection for approximation algorithms.

## Related Concepts

- [[Dynamic Programming]] — explores all subproblem combinations; greedy is a restricted, faster form.
- [[Divide and Conquer]] — a different paradigm that splits problems into independent subproblems.
- [[Dijkstra's Algorithm]] — a canonical greedy algorithm for shortest paths.
- [[Minimum Spanning Tree]] — solved optimally by greedy methods (Kruskal, Prim).
- [[Backtracking]] — greedy is the opposite; it never backtracks.

## Limitations

- Proving optimality can be difficult.
- Many important problems do not satisfy the greedy choice property.
- Even when optimal, the proof of optimality is often non-trivial (exchange argument, induction).
