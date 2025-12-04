# AI Reasoning

## Table of Contents

[[01-agents|Agents]]
[[02-uninformed_search_algorithms|Uninformed Search Algorithms]]
[[03-heuristic_algorithms|Heuristic Algorithms]]
[[04-first_order_logic|First Order Logic]]
[[05-knowledge_representation|Knowledge Representation]]

## Course Overview

This course covers fundamental concepts in artificial intelligence, focusing on search algorithms, knowledge representation, and logical reasoning. Students learn how to formulate problems, design intelligent agents, and implement various search and reasoning techniques.

---

## Table of Contents

### Core Topics

1. [[Agents|Agent Formulation]]
   - Problem components (state space, actions, goals)
   - State space representation
   - Initial and goal states
   - Transition models and action costs
   - Solution concepts and path optimization

2. [[Uninformed_Search_Algorithms|Uninformed Search Algorithms]]
   - Breadth-First Search (BFS)
   - Depth-First Search (DFS)
   - Dijkstra's Algorithm
   - Backtracking
   - Complexity and efficiency comparisons

3. [[Heuristic_Algorithms|Heuristic Search Algorithms]]
   - A* Search
   - Greedy Best-First Search
   - Heuristic functions and admissibility
   - Consistency and optimality
   - Hill climbing and local search

4. [[Knowledge_Representation|Knowledge Representation]]
   - Propositional logic
   - Semantic networks
   - Frames and ontologies
   - Production rules
   - Reasoning with uncertainty

5. [[First_Order_Logic|First-Order Logic]]
   - Predicates and quantifiers
   - Inference rules
   - Unification and resolution
   - Knowledge bases
   - Theorem proving

---

## Key Concepts

### Problem Solving
- **Search spaces**: Graphs representing possible states
- **Search strategies**: Systematic exploration techniques
- **Optimality**: Finding best solutions
- **Completeness**: Guaranteeing solution discovery

### Knowledge and Reasoning
- **Representation**: Encoding knowledge formally
- **Inference**: Deriving new knowledge
- **Uncertainty**: Handling incomplete information
- **Logic**: Formal reasoning systems

### Agent Design
- **Rationality**: Choosing optimal actions
- **Environment types**: Observable, deterministic, episodic
- **Agent architectures**: Reactive, deliberative, hybrid
- **Performance measures**: Evaluating agent behavior

---

## Applications

- Autonomous navigation and robotics
- Game playing (chess, Go, poker)
- Route planning and logistics
- Medical diagnosis systems
- Natural language understanding
- Automated theorem proving
- Expert systems

---

## Prerequisites

- Data structures and algorithms
- Discrete mathematics
- Logic fundamentals
- Programming proficiency (Python recommended)

---

## Learning Objectives

By the end of this course, you should be able to:
1. Formulate real-world problems as search problems
2. Implement and compare various search algorithms
3. Design and evaluate heuristic functions
4. Represent knowledge using logical formalisms
5. Perform inference in propositional and first-order logic
6. Build intelligent agents for specific domains
7. Analyze algorithm complexity and optimality
8. Apply AI techniques to practical problems

---

## Algorithms Summary

### Search Algorithms

| Algorithm | Complete | Optimal | Time Complexity | Space Complexity |
|-----------|----------|---------|-----------------|------------------|
| BFS | Yes | Yes* | O(b^d) | O(b^d) |
| DFS | No | No | O(b^m) | O(bm) |
| Dijkstra | Yes | Yes | O(E log V) | O(V) |
| A* | Yes | Yes** | O(b^d) | O(b^d) |

*For unit costs  
**With admissible heuristic

---

## Further Topics

This course prepares you for advanced AI topics:
- Machine learning and neural networks
- Natural language processing
- Computer vision
- Reinforcement learning
- Multi-agent systems
- Planning and scheduling
