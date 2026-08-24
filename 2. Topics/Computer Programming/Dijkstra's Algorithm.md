# Dijkstra's Algorithm

Dijkstra's algorithm is an algorithm for finding the shortest paths between nodes in a weighted graph. It maintains a set of unvisited nodes and calculates the tentative distance from the source to every other node, always choosing the node with the smallest distance.

## Overview

Named after Dutch computer scientist Edsger W. Dijkstra (1956), this algorithm solves the single-source shortest path problem for graphs with non-negative edge weights. It is a cornerstone of network routing and navigation systems.

## Algorithm

1. Assign a distance of 0 to the source node and infinity to all other nodes.
2. Mark all nodes as unvisited.
3. While unvisited nodes remain:
   - Select the unvisited node with the smallest tentative distance.
   - For each of its neighbors, calculate the tentative distance through the current node. If smaller than the stored value, update it.
   - Mark the current node as visited.

### Pseudocode

```
Dijkstra(graph, source):
    dist[source] = 0
    for each vertex v != source:
        dist[v] = infinity
    PQ = priority queue ordered by dist
    PQ.insert(source, 0)
    while PQ is not empty:
        u = PQ.extract_min()
        for each neighbor v of u:
            alt = dist[u] + weight(u, v)
            if alt < dist[v]:
                dist[v] = alt
                PQ.decrease_key(v, alt)
    return dist
```

## Complexity

- **Naive implementation** (array-based minimum search): $$O(V^2)$$
- **Binary heap + adjacency list**: $$O((V + E) \log V) = O(E \log V)$$
- **Fibonacci heap**: $$O(V \log V + E)$$
- **Space complexity**: $$O(V)$$ for distance array and priority queue.

## Properties

- Only works correctly with **non-negative edge weights**.
- It is a [[Greedy Algorithms|greedy algorithm]]: it always picks the locally optimal (smallest distance) node.
- Once a node is marked visited, its shortest path distance is finalized.
- Dijkstra's algorithm computes a shortest-path tree rooted at the source.

## Applications

- **GPS navigation** (Google Maps, Waze).
- **Network routing protocols** (OSPF — Open Shortest Path First).
- **Social network analysis** (finding shortest connections).
- **Robotics** (path planning in weighted grids).
- **Transportation and logistics** (minimizing fuel cost or travel time).

## Variants

- **A\* search**: extends Dijkstra with a heuristic to guide search toward a target, often dramatically faster.
- **Bidirectional Dijkstra**: runs Dijkstra from both source and target simultaneously, stopping when the frontiers meet.
- **Dial's algorithm**: uses bucket queues for integer-weighted graphs, achieving $$O(V + E + W)$$ where $$W$$ is the maximum weight.

## Limitations

- Fails on graphs with **negative edge weights** — use the [[Bellman-Ford Algorithm]] instead.
- Cannot handle negative cycles (the shortest path is undefined).
- For unweighted graphs, [[Breadth First Search]] is simpler and faster ($$O(V+E)$$).
- The binary heap version has a logarithmic factor that can be significant on very large graphs.

## Related Concepts

- [[Breadth First Search]] — Dijkstra's algorithm generalized for weighted graphs.
- [[Greedy Algorithms]] — Dijkstra is a canonical example of greedy optimization.
- [[Priority Queue|Priority Queues]] — the essential data structure for efficiently selecting the minimum-distance node.
- [[Bellman-Ford Algorithm]] — handles negative edge weights at the cost of $$O(VE)$$ time.
- [[A* Search Algorithm]] — a heuristic-driven variant for goal-directed search.
