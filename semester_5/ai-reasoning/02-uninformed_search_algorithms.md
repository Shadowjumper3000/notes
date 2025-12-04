> Informed refers to knowing how "close" we are to the goal

### Important uninformed search algorithms:
- Breadth-first search
- Dijkstra or uninform-cost search
- Depth-limited search
- Iterative deepening
- Bi-direction search

---

## BFS (Breadth-First Search)
- **Approach**: Level-order traversal using a queue.
- **Time Complexity**:  
  - O(V + E) (adjacency list)  
  - O(V²) (adjacency matrix)
- **Space Complexity**:  
  - O(V) for visited + queue  
- **Use cases**: Shortest path in unweighted graphs, level-order processing.

---

## DFS (Depth-First Search)
- **Approach**: Recursive/iterative traversal using stack (implicit/explicit).
- **Time Complexity**:  
  - O(V + E) (adjacency list)  
  - O(V²) (adjacency matrix)
- **Space Complexity**:  
  - O(V) for visited + recursion/stack depth  
- **Use cases**: Connectivity, cycle detection, topological sorting.

---

## Dijkstra’s Algorithm
- **Approach**: Greedy shortest-path using priority queue.
- **Time Complexity**:  
  - O((V + E) log V) with binary heap  
  - O(V²) with naive array
- **Space Complexity**:  
  - O(V) for distance + priority queue  
- **Use cases**: Shortest path in weighted graphs (non-negative weights).

---

## Backtracking
- **Approach**: Recursive search with state undo (explore + backtrack).
- **Time Complexity**: Exponential in worst-case (O(b^d), branching factor b, depth d).  
- **Space Complexity**: O(d) for recursion stack.  
- **Use cases**: Constraint satisfaction (N-Queens, Sudoku, permutations).

---

## Memory Usage Comparisons
- **BFS**: High memory (queue holds entire frontier). Worst: O(V).  
- **DFS**: Low memory (stack depth ≤ V). Worst: O(V).  
- **Dijkstra**: Depends on PQ implementation; O(V + E).  
- **Backtracking**: Depends on depth; typically O(d).  

---

## Efficiency Summary
- **BFS**: Good for unweighted shortest path, but memory-heavy on wide graphs.  
- **DFS**: Space-efficient, not optimal for shortest path.  
- **Dijkstra**: Optimal for weighted graphs, heavier due to PQ ops.  
- **Backtracking**: Expensive, but only feasible with pruning/constraints.

