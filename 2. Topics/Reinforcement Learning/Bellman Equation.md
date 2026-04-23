**Tags:** #concept #rl
**Related:** [[State Value Function]], [[Action Value Function]], [[Markov Decision Process]], [[Bellman Optimality Equation]]

## Overview

The Bellman equation is a recursive decomposition for the value function of a specific policy $\pi$. It establishes a fundamental relationship between the value of a state and the values of its successor states, serving as the cornerstone for solving Markov Decision Processes (MDPs). By expressing the value of the current state in terms of immediate rewards and discounted future expectations, the Bellman equation provides a self-consistent condition that any valid value function must satisfy. It is the mathematical bridge that allows algorithms to iteratively update state estimates (bootstrapping) without waiting for the full trajectory of experience to conclude.

## Technical Depth

The Bellman equation for a policy $\pi$ relates the state-value function $v_\pi(s)$ to the values of its potential next states. It is derived from the definition of return $G_t = R_{t+1} + \gamma G_{t+1}$:

$$v_\pi(s) = \mathbb{E}_\pi[G_t \mid S_t = s] = \sum_a \pi(a|s) \sum_{s',r} p(s',r|s,a)\left[r + \gamma\, v_\pi(s')\right]$$

This equation shows that the value of state $s$ is the average over all possible actions $a$ and subsequent states $s'$ of the immediate reward $r$ plus the discounted value of the next state $\gamma v_\pi(s')$. Similarly, for the action-value function $q_\pi(s,a)$, the Bellman equation is:

$$q_\pi(s,a) = \sum_{s',r} p(s',r|s,a)\left[r + \gamma \sum_{a'} \pi(a'|s')\, q_\pi(s',a')\right]$$

Mathematically, the Bellman equation is a system of $|\mathcal{S}|$ linear equations where the state values are the unknowns. In a vector-matrix form, it is expressed as $\mathbf{v}_\pi = \mathbf{r}_\pi + \gamma \mathbf{P}_\pi \mathbf{v}_\pi$, where $\mathbf{r}_\pi$ is the expected immediate rewards and $\mathbf{P}_\pi$ is the transition matrix under policy $\pi$. Because the discount factor $\gamma < 1$, the Bellman operator is a contraction mapping, ensuring that iterative application (as seen in Policy Evaluation) will always converge to a unique fixed-point solution.

## Applications/Examples

- **Policy Evaluation:** The Bellman equation is the iterative core of algorithms that calculate the value function for a fixed policy, such as in Dynamic Programming or Temporal Difference (TD) learning.
- **TD Learning:** $v(s_t) \approx r_{t+1} + \gamma v(s_{t+1})$ is a direct stochastic approximation of the Bellman equation used in online RL.
- **Bootstrapping:** The recursive nature of the equation allows algorithms like SARSA and Q-Learning to learn from partial trajectories by updating current estimates using subsequent estimates.
- **Optimal Control:** In engineering and economics, the Bellman equation is used to solve multi-stage decision problems, where it is often referred to as the **Bellman Optimality Equation** for the optimal policy.

## References

- **Sutton, R. S., & Barto, A. G. (2018).** *Reinforcement Learning: An Introduction*. MIT Press. (Chapter 3: Bellman Equations).
- **Bellman, R. (1957).** *Dynamic Programming*. Princeton University Press. (The original source of the concept).
- **Bertsekas, D. P. (2012).** *Dynamic Programming and Optimal Control*. Athena Scientific.
