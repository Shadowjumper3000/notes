# Linked Lists

A linked list is a linear data structure where elements are stored in nodes. Each node contains a data field and a reference (link) to the next node in the sequence, allowing for efficient insertion and deletion.

## Overview

Unlike [[Arrays|arrays]], linked lists do not store elements in contiguous memory. They consist of dynamically allocated nodes connected by pointers, enabling constant-time insertions and deletions at known positions.

## Types of Linked Lists

### Singly Linked List
Each node holds a pointer to the next node. Traversal is forward-only.

```
[data | next] -> [data | next] -> [data | null]
```

### Doubly Linked List
Each node holds pointers to both the next and previous nodes. Enables bidirectional traversal and $$O(1)$$ deletion of a node given only its reference.

```
null <- [prev | data | next] <-> [prev | data | next] -> null
```

### Circular Linked List
The last node points back to the first (or head), forming a loop. Useful for round-robin scheduling.

## Complexity

| Operation | Singly Linked | Doubly Linked |
|-----------|---------------|---------------|
| Access (index) | $$O(n)$$ | $$O(n)$$ |
| Search | $$O(n)$$ | $$O(n)$$ |
| Insert at head | $$O(1)$$ | $$O(1)$$ |
| Insert at tail | $$O(1)$$ with tail ptr | $$O(1)$$ |
| Delete at head | $$O(1)$$ | $$O(1)$$ |
| Delete given node | $$O(1)$$ with prev | $$O(1)$$ |

## Applications

- **Implementation of stacks and queues** (especially with doubly linked lists).
- **Undo/redo functionality** in editors (doubly linked list of states).
- **Adjacency lists** in graph representations.
- **Hash table chaining** (collision resolution via linked lists).
- **Music playlist** navigation (next/previous tracks).
- **Memory management** (free lists in allocators).

## Variants

- **Skip list**: layered linked list with express lanes for $$O(\log n)$$ average search.
- **XOR linked list**: memory-efficient doubly linked list using XOR of previous and next pointers.
- **Unrolled linked list**: each node stores a small array of elements to improve cache locality.
- **Self-organizing list**: reorders elements on access to improve average lookup time (move-to-front heuristic).

## Trade-offs vs Arrays

| Aspect | Linked List | Array |
|--------|-------------|-------|
| Memory allocation | Dynamic per node | Contiguous block |
| Access time | $$O(n)$$ | $$O(1)$$ |
| Insert/delete at head | $$O(1)$$ | $$O(n)$$ |
| Memory overhead | Extra pointer(s) per element | None |
| Cache locality | Poor (scattered nodes) | Excellent |

## Related Concepts

- [[Arrays]] — the alternative contiguous linear data structure.
- [[Stacks]] — can be implemented with a singly linked list (LIFO).
- [[Queues]] — can be implemented with a doubly linked list (FIFO).
- [[Hash Tables]] — use linked lists for chaining.
- [[Data Structures]] — linked lists are a foundational building block.
- [[Recursion]] — many linked list operations (reverse, merge) are elegantly expressed recursively.

## Limitations

- **No random access**: accessing the $$k$$-th element requires $$O(k)$$ time.
- **Memory overhead**: each node requires extra space for one or two pointers.
- **Poor cache performance**: nodes may be scattered across memory, reducing spatial locality.
- **Pointer-related bugs**: null pointer dereferences, memory leaks, and dangling pointers are common in manual implementations.
- **Reverse traversal** is expensive or requires extra pointers (doubly linked).
