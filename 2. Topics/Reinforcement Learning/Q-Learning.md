**Tags:** #concept #rl
**Related:** [[Temporal Difference Learning]], [[SARSA]], [[Expected SARSA]], [[Bellman Optimality Equation]]

## Overview

Q-learning is a seminal reinforcement learning algorithm that enables an agent to learn the value of its actions in a given state without requiring a model of the environment. As an **off-policy** temporal difference (TD) control method, Q-learning directly estimates the optimal action-value function ($q_*$), regardless of the agent's current exploration strategy. This decoupling of the behavioral policy from the learned target policy makes it a robust and versatile tool for solving complex discrete-action problems, serving as the historical and theoretical foundation for much of modern deep reinforcement learning.

## Technical Depth

The primary objective of Q-learning is to approximate the optimal action-value function $Q(s, a)$, which represents the maximum expected discounted return starting from state $s$ and taking action $a$. The update rule is derived from the **Bellman Optimality Equation**:

$$Q(s_t, a_t) \leftarrow Q(s_t, a_t) + \alpha \left[ r_{t+1} + \gamma \max_{a'} Q(s_{t+1}, a') - Q(s_t, a_t) \right]$$

In this update, $r_{t+1} + \gamma \max_{a'} Q(s_{t+1}, a')$ is the **target**, representing a one-step estimate of the optimal future value. The presence of the $\max_{a'}$ operator is what makes Q-learning off-policy: the algorithm assumes that the agent will take the best possible action in the next state, even if the actual behavior policy (e.g., $\epsilon$-greedy) chooses a random exploratory action.

For convergence, Q-learning requires that all state-action pairs $(s, a)$ are visited an infinite number of times and that the step size $\alpha$ satisfies the standard Robbins-Monro conditions ($\sum \alpha_t = \infty$ and $\sum \alpha_t^2 < \infty$). In practice, Q-learning is known to exhibit a **maximization bias** because it uses the maximum estimated value as a proxy for the maximum true value, which can lead to significant overestimations. This issue is often addressed in advanced implementations like **Double Q-learning**.

## Applications/Examples

- **Gridworld and Pathfinding:** Q-learning is a standard baseline for solving environments like FrozenLake or Cliff Walking, where the agent learns to navigate a grid while avoiding hazards.
- **Deep Q-Networks (DQN):** The principles of Q-learning were scaled to high-dimensional sensory inputs (like Atari pixels) by replacing the Q-table with a deep neural network, as demonstrated in DeepMind's breakthrough 2015 research.
- **Supply Chain Management:** Q-learning is used to optimize order quantities and inventory levels by learning from historical demand fluctuations.
- **Traffic Light Control:** Agents use Q-learning to dynamically adjust signal timings based on real-time vehicle flow, reducing congestion in urban environments.

## References

- **Watkins, C. J., & Dayan, P. (1992).** *Q-learning*. Machine Learning, 8(3-4), 279-292. (The original paper introducing the algorithm).
- **Sutton, R. S., & Barto, A. G. (2018).** *Reinforcement Learning: An Introduction*. MIT Press. (Chapter 6: Temporal-Difference Learning).
- **Mnih, V., et al. (2015).** *Human-level control through deep reinforcement learning*. Nature. (Introduces DQN).
