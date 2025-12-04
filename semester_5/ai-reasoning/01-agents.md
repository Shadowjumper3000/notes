# Formulation of Agent Problems

## Problem Components

### 1. State Space
The **state space** defines all possible configurations that the agent can occupy.  
Each state represents a unique situation or condition within the environment.

### 2. Initial State
The **initial state** is the starting point of the agent in the state space.  
It defines where problem solving or search begins.

### 3. Goal States
A **goal state** (or set of goal states) represents the desired condition(s) the agent aims to reach.  
A predicate function **IS-GOAL(s)** determines whether a given state satisfies the goal condition.

### 4. Actions
For each state, there exists a finite set of **available actions** that the agent can execute.  
These actions define possible transitions to successor states.

### 5. Transition Model
The **transition model** specifies the outcome of each action.  
Formally:  
`RESULT(s, a) = s'`  
where performing action `a` in state `s` leads to the new state `s'`.

### 6. Action Cost Function
Each transition has an associated **action cost** that quantifies the expense or effort required.  
Defined as:  
`ACTION-COST(s, a, s')` or `c(s, a, s')`  
The cost function should align with the agent’s performance measure, guiding optimization toward efficient or optimal paths.

---

## Solution Concepts

### Path
A **path** is a sequence of states connected by actions:
