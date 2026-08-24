# Recursion

Recursion is a method of solving a problem where the solution depends on solutions to smaller instances of the same problem. In programming, this involves a function calling itself until it reaches a base case.

## Overview

Recursion is a fundamental technique in computer science, deeply connected to mathematical induction. It appears in algorithm design, data structure traversal, and language theory. Every recursive solution consists of a **base case** (termination condition) and a **recursive case** (reduction toward the base case).

## Structure

A recursive function has two essential components:

1. **Base case**: the simplest instance of the problem, solved directly without recursion.
2. **Recursive case**: breaks the problem into smaller subproblems and calls itself on them.

### Example: Factorial

```
factorial(n):
    if n == 0 or n == 1:
        return 1              // base case
    return n * factorial(n-1) // recursive case
```

## The Call Stack

Each recursive call pushes a new frame onto the call stack, containing local variables and the return address. When the base case is reached, frames unwind (return) in reverse order.

- **Depth**: the maximum number of stack frames is proportional to the recursion depth.
- **Stack overflow**: occurs when recursion depth exceeds the available stack memory (common in deep recursion).

## Recurrence Relations

Recurrence relations express the time complexity of recursive algorithms. For example, [[Merge Sort]]:

$$T(n) = 2T(n/2) + O(n)$$

Solving via the master theorem yields $$T(n) = O(n \log n)$$.

### Common Recurrences

| Algorithm | Recurrence | Complexity |
|-----------|------------|------------|
| Binary Search | $$T(n) = T(n/2) + O(1)$$ | $$O(\log n)$$ |
| Merge Sort | $$T(n) = 2T(n/2) + O(n)$$ | $$O(n \log n)$$ |
| Fibonacci (naive) | $$T(n) = T(n-1) + T(n-2) + O(1)$$ | $$O(2^n)$$ |
| Tree traversal | $$T(n) = 2T(n/2) + O(1)$$ | $$O(n)$$ |

## Tail Recursion

A recursive call is **tail-recursive** if it is the last operation performed by the function. Tail-recursive functions can be optimized by the compiler into iteration (tail-call optimization), reusing the same stack frame.

```
// Tail-recursive factorial
factorial_tail(n, acc):
    if n == 0:
        return acc
    return factorial_tail(n-1, n * acc)
```

## Applications

- **Tree and graph traversal** ([[Depth First Search]], binary tree traversals).
- **Divide and conquer algorithms** ([[Merge Sort]], [[Quicksort]], [[Binary Search]]).
- **Backtracking** (N-Queens, Sudoku, [[Breadth First Search#Variants|pathfinding]]).
- **Dynamic programming** (top-down memoization).
- **Parsing** of recursive grammars (JSON, XML, programming languages).
- **Fractal generation** (mathematical self-similarity).
- **Functional programming** (recursion replaces loops in purely functional languages).

## Variants

- **Linear recursion**: at most one recursive call per case (e.g., factorial).
- **Tree recursion**: multiple recursive calls per case (e.g., Fibonacci).
- **Mutual recursion**: two or more functions call each other recursively (e.g., even/odd checkers).
- **Nested recursion**: a recursive call appears as an argument to another recursive call (Ackermann function).

## Related Concepts

- [[Iteration]] — repetition via loops; recursion can always be simulated with an explicit stack.
- [[Divide and Conquer]] — an algorithmic paradigm that relies on recursion.
- [[Dynamic Programming]] — recursion with memoization to avoid redundant work.
- [[Depth First Search]] — a canonical recursive graph traversal.
- [[Stacks]] — recursion implicitly uses the call stack.
- [[Master Theorem]] — tool for analyzing the complexity of recursive algorithms.

## Limitations

- **Stack overflow**: deep recursion may exceed stack limits; iterative solutions avoid this.
- **Performance overhead**: function call overhead and repeated computation (mitigated by memoization in [[Dynamic Programming]]).
- **Readability**: not all problems are naturally recursive; overuse can harm code clarity.
- **Debugging difficulty**: tracing deep recursive calls can be complex.
- **No tail-call optimization**: many languages (Python, Java) do not optimize tail recursion, making it as memory-intensive as non-tail recursion.
