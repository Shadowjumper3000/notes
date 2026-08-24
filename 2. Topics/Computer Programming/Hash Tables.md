# Hash Tables

A hash table is a data structure that implements an associative array abstract data type, mapping keys to values using a hash function to compute an index into an array of buckets or slots.

## Overview

Hash tables offer average-case $$O(1)$$ lookup, insertion, and deletion — among the fastest possible for key-value storage. They are ubiquitous in systems programming, databases, and language runtimes.

## Core Concepts

### Hash Function
A function $$h: K \to \{0, 1, \dots, m-1\}$$ that maps a key from the universe $$K$$ to an index in a table of size $$m$$. A good hash function distributes keys uniformly.

### Collision
When two distinct keys hash to the same index. Handling collisions is central to hash table design.

### Load Factor
$$\alpha = \frac{n}{m}$$ where $$n$$ is the number of keys stored and $$m$$ is the number of buckets. A higher load factor increases collision probability and degrades performance.

## Collision Resolution

### Chaining
Each bucket stores a linked list of entries. On collision, the new entry is appended to the list at that bucket.

- **Time**: $$O(\alpha)$$ average, $$O(n)$$ worst case.

### Open Addressing
All entries are stored directly in the table array. On collision, probe for the next empty slot.

- **Linear probing**: $$h(k, i) = (h(k) + i) \bmod m$$
- **Quadratic probing**: $$h(k, i) = (h(k) + c_1 i + c_2 i^2) \bmod m$$
- **Double hashing**: $$h(k, i) = (h_1(k) + i \cdot h_2(k)) \bmod m$$

## Complexity

| Operation | Average | Worst Case |
|-----------|---------|------------|
| Search    | $$O(1)$$ | $$O(n)$$ |
| Insert    | $$O(1)$$ | $$O(n)$$ |
| Delete    | $$O(1)$$ | $$O(n)$$ |

Worst case occurs when all keys collide (poor hash function or adversarial input). **Resizing** (rehashing) is an amortized $$O(1)$$ operation.

## Applications

- **Symbol tables** in compilers and interpreters.
- **Database indexing** (hash indexes for equality lookups).
- **Caching** (memcached, Redis, CPU caches).
- **Implementing sets** and dictionaries in programming languages.
- **Password verification** (storing password hashes).
- **Bloom filters** (probabilistic membership tests using hash functions).

## Variants

- **Cuckoo hashing**: uses two hash functions and relocates existing keys on collision, guaranteeing $$O(1)$$ worst-case lookup.
- **Robin Hood hashing**: open addressing variant that reduces probe length variance by swapping entries.
- **Hopscotch hashing**: combines aspects of cuckoo and open addressing for cache-friendly performance.
- **Perfect hashing**: constructs a collision-free hash function for a static set of keys.
- **Consistent hashing**: used in distributed systems to minimize re-mapping when the table size changes.

## Related Concepts

- [[Arrays]] — the underlying storage for most hash tables.
- [[Linked Lists]] — commonly used for chaining-based collision resolution.
- [[Data Structures]] — hash tables are a fundamental data structure.
- [[Bloom Filters]] — a space-efficient probabilistic structure based on hashing.

## Limitations

- **No ordering**: hash tables do not maintain sorted order of keys (use [[Binary Search Tree|balanced BSTs]] instead).
- **Worst-case performance**: adversarial inputs can cause $$O(n)$$ behavior if the hash function is known.
- **Memory overhead**: open addressing wastes empty slots; chaining uses extra pointers.
- **Resizing cost**: resizing the table requires rehashing all entries, which is an $$O(n)$$ operation (though amortized).
- **Not efficient for range queries**: hash tables cannot support efficient range scans or prefix lookups.
