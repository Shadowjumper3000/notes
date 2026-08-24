# Breadth First Search (BFS)

Breadth-First Search is a graph traversal algorithm that explores all neighbor nodes at the present depth prior to moving on to the nodes at the next depth level. It uses a [[Queues|queue]] data structure to track nodes to be visited.

## Overview

BFS is one of the fundamental graph traversal algorithms, along with [[Depth First Search]]. It systematically explores a graph level by level, guaranteeing that the shortest path (in terms of number of edges) is found in an unweighted graph.

## Algorithm

1. Start at a source node and mark it as visited.
2. Enqueue the source node.
3. While the queue is not empty:
   - Dequeue a node.
   - Process it.
   - Enqueue all unvisited adjacent nodes and mark them as visited.

### Pseudocode

```
BFS(graph, start):
    visited = set()
    queue = Queue()
    visited.add(start)
    queue.enqueue(start)
    while queue is not empty:
        node = queue.dequeue()
        for neighbor in graph.adjacent(node):
            if neighbor not in visited:
                visited.add(neighbor)
                queue.enqueue(neighbor)
```

## Complexity

- **Time complexity**: $$O(V + E)$$, where $$V$$ is the number of vertices and $$E$$ is the number of edges. Every vertex and every edge is explored once.
- **Space complexity**: $$O(V)$$, for the queue and the visited set. In the worst case, the queue may hold all vertices.

## Properties

- BFS always finds the shortest path in an unweighted graph.
- It can be used to detect cycles in both directed and undirected graphs.
- BFS on a tree is equivalent to level-order traversal.
- BFS is a complete algorithm: it will find a solution if one exists.

## Applications

- **Shortest path** in unweighted graphs (e.g., social network degrees of separation).
- **Web crawling**: search engines use BFS to discover web pages by following links.
- **GPS navigation**: finding nearby locations.
- **Puzzle solving**: solving Rubik's Cube or sliding puzzles with the fewest moves.
- **Connected components**: finding all nodes in a connected component using BFS.
- **Bipartite graph checking**: a graph is bipartite if and only if BFS finds no odd-length cycle.

## Variants

- **Bidirectional BFS**: runs two simultaneous BFS searches (one from source, one from target) to reduce search space.
- **Lexicographic BFS**: orders the neighbors during traversal to produce a canonical ordering, useful in chordal graph recognition.
- **Multi-source BFS**: starts from multiple source nodes simultaneously, useful in problems like "distance to the nearest hospital."

## Related Concepts

- [[Depth First Search]] — BFS's counterpart; uses a stack instead of a queue.
- [[Dijkstra's Algorithm]] — generalizes BFS to weighted graphs.
- [[Greedy Algorithms]] — BFS is sometimes considered a greedy approach to finding the shortest path.
- [[Queue|Queues]] — the fundamental data structure powering BFS.

## Limitations

- BFS can be memory-intensive for wide graphs because it must store all nodes at the current level in the queue.
- BFS does not naturally work for weighted graphs; [[Dijkstra's Algorithm]] is the appropriate generalization.
