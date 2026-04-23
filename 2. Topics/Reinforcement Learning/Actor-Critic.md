**Tags:** #concept #rl
**Related:** [[Actor-Critic Methods]], [[Policy Gradient Methods]], [[Advantage Function]], [[Baseline in Policy Gradients]], [[Temporal Difference Learning]], [[State Value Function]]

## Overview
The Actor-Critic architecture is a hybrid reinforcement learning framework that combines the strengths of both value-based and policy-based methods. It splits the learning agent into two distinct components: the **Actor**, which is responsible for selecting actions by maintaining a parameterized policy, and the **Critic**, which evaluates the actions taken by the actor by estimating a value function. This separation addresses the limitations of both pure policy gradients (which often suffer from high variance) and pure value-based methods (which can be unstable when used with function approximation). By utilizing the critic's value estimate as a reinforcement signal, the actor-critic method can learn more efficiently, providing a bridge between Monte Carlo methods and Temporal Difference learning.

## Technical Depth
The architecture operates by updating both components simultaneously using the environment's feedback. The Actor's policy $\pi_\theta(a|s)$ is typically updated using the gradient of the performance objective, while the Critic's value function $v_w(s)$ (or action-value function $q_w(s,a)$) is updated to minimize the temporal difference error.

A key development in modern actor-critic methods is the use of the **Advantage Function** $A(s,a) = Q(s,a) - V(s)$. The advantage function quantifies how much better an action $a$ is compared to the average action in state $s$. In the **Advantage Actor-Critic (A2C/A3C)** variant, the TD error $\delta_t = R_{t+1} + \gamma V_w(S_{t+1}) - V_w(S_t)$ serves as an unbiased estimate of the advantage.

The update rules for a one-step actor-critic are:
1.  **Critic Update (Value Function):**
    $$w \leftarrow w + \alpha_w \delta_t \nabla_w V_w(S_t)$$
    where $\delta_t = R_{t+1} + \gamma V_w(S_{t+1}) - V_w(S_t)$ is the TD error.
2.  **Actor Update (Policy):**
    $$\theta \leftarrow \theta + \alpha_\theta \delta_t \nabla_\theta \ln \pi_\theta(A_t|S_t)$$

This formulation significantly reduces variance compared to REINFORCE by replacing the full return $G_t$ with the critic's estimate, while the use of bootstrapping (through $V_w(S_{t+1})$) allows for fully online, incremental learning. More advanced versions, such as **Proximal Policy Optimization (PPO)** and **Soft Actor-Critic (SAC)**, incorporate additional constraints or objectives to ensure stable updates and efficient exploration.

## Applications/Examples
Actor-critic methods are the dominant choice for complex, high-dimensional, and continuous control tasks:
- **Robotic Control:** Algorithms like **DDPG (Deep Deterministic Policy Gradient)** and **SAC** are used to train robots for manipulation, walking, and flying, where actions are continuous torque or velocity commands.
- **Autonomous Driving:** A3C has been used to train agents in simulated environments (like CARLA) to handle complex maneuvers by processing sensor inputs and outputting continuous steering and acceleration values.
- **Game AI:** OpenAI's Five (for Dota 2) and DeepMind's AlphaStar (for StarCraft II) utilized massive-scale actor-critic architectures (variants of PPO and A3C) to achieve professional-level play.
- **Resource Management:** Actor-critic methods help in optimizing data center cooling and network traffic routing by evaluating the long-term impact of allocation decisions.

## References
- **Sutton, R. S., & Barto, A. G. (2018).** *Reinforcement Learning: An Introduction*. MIT Press. (Chapter 13).
- **Mnih, V., et al. (2016).** *Asynchronous methods for deep reinforcement learning*. ICML. (Foundational paper for A3C).
- **Konda, V. R., & Tsitsiklis, J. N. (2000).** *Actor-critic algorithms*. Advances in Neural Information Processing Systems (NIPS).
- **Haarnoja, T., et al. (2018).** *Soft actor-critic: Off-policy maximum entropy deep reinforcement learning with a stochastic actor*. ICML. (SAC foundation).
