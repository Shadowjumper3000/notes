# Depth First Search (DFS)

Depth-First Search is a graph traversal algorithm that starts at the root node and explores as far as possible along each branch before backtracking. It uses a [[Stacks|stack]] data structure (often implicitly via [[Recursion]]) to track nodes.

## Overview

DFS is a fundamental graph traversal algorithm that prioritizes depth over breadth. Unlike [[Breadth First Search]], which explores level by level, DFS plunges down a single path until it can go no further, then backtracks.

## Algorithm

1. Start at a source node and mark it as visited.
2. Push the source node onto a stack.
3. While the stack is not empty:
   - Pop a node.
   - Process it.
   - Push all unvisited adjacent nodes onto the stack and mark them as visited.

### Recursive Pseudocode

```
DFS(graph, node, visited):
    visited.add(node)
    for neighbor in graph.adjacent(node):
        if neighbor not in visited:
            DFS(graph, neighbor, visited)
```

### Iterative Pseudocode (using explicit stack)

```
DFS(graph, start):
    visited = set()
    stack = Stack()
    stack.push(start)
    while stack is not empty:
        node = stack.pop()
        if node not in visited:
            visited.add(node)
            for neighbor in graph.adjacent(node):
                if neighbor not in visited:
                    stack.push(neighbor)
```

## Complexity

- **Time complexity**: $$O(V + E)$$, where $$V$$ is the number of vertices and $$E$$ is the number of edges.
- **Space complexity**: $$O(V)$$ in the worst case. For the recursive implementation, the call stack can grow to the depth of the graph (which could be $$O(V)$$ for a long path). The iterative version uses an explicit stack of similar size.

## Properties

- DFS is not guaranteed to find the shortest path in an unweighted graph.
- It naturally performs a topological ordering of a directed acyclic graph (DAG) via finishing times.
- DFS can detect cycles using node coloring (white, gray, black).
- A single DFS run can compute connected components, strongly connected components, and articulation points.

## Applications

- **Topological sorting** of [[DAG|DAGs]].
- **Cycle detection** in graphs.
- **Connected components** and [[Strongly Connected Components]] (Kosaraju's or Tarjan's algorithm).
- **Pathfinding in mazes**.
- **Bipartite graph checking**.
- **Tree traversals**: pre-order, in-order, post-order.
- **Backtracking algorithms**: solving Sudoku, N-Queens, and constraint satisfaction problems.
- **Garbage collection** in programming languages (mark-and-sweep).

## Variants

- **Pre-order DFS**: processes the current node before its children.
- **Post-order DFS**: processes children before the current node.
- **In-order DFS**: for binary trees, visits left subtree, then node, then right subtree.
- **Iterative Deepening DFS (IDDFS)**: combines DFS's space efficiency with BFS's completeness by running DFS to increasing depth limits.

## Related Concepts

- [[Breadth First Search]] — the level-order counterpart to DFS.
- [[Recursion]] — DFS is naturally expressed recursively.
- [[Stacks]] — the core data structure for DFS iteration.
- [[Backtracking]] — a closely related algorithmic technique that uses DFS as its engine.
- [[Dijkstra's Algorithm]] — for weighted graph shortest paths.

## Limitations

- Recursive DFS can overflow the call stack for very deep graphs.
- DFS may explore an extremely deep (even infinite) branch when a solution is shallow nearby — IDDFS addresses this.
- It does not produce shortest paths in unweighted or weighted graphs.
