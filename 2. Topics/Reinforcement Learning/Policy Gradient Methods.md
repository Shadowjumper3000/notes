**Tags:** #concept #rl
**Related:** [[Policy Gradients]], [[RL Policy]], [[Policy Gradient Theorem]], [[Stochastic Policy Gradient]], [[Actor-Critic Methods]]

## Overview

Policy gradient methods represent a powerful class of reinforcement learning algorithms that directly parameterize and optimize an agent's policy $\pi(a|s, \theta)$ instead of learning value functions to infer a policy indirectly. By performing gradient ascent on a performance measure $J(\theta)$, these methods move the policy parameters in the direction that maximizes the expected return. This direct optimization approach is particularly effective in high-dimensional or continuous action spaces where computing the maximum over all actions, as required in value-based methods like Q-learning, would be computationally prohibitive.

## Technical Depth

The mathematical foundation for these algorithms is the **Policy Gradient Theorem**, which provides an expression for the gradient of the performance measure with respect to the policy parameters $\theta$:

$$\nabla J(\theta) \propto \sum_s \mu(s) \sum_a q_\pi(s,a) \nabla \pi(a|s,\theta)$$

where $\mu(s)$ is the on-policy distribution under $\pi$. In its simplest form, the REINFORCE algorithm estimates this gradient using the **likelihood ratio trick** (or score function) to convert the gradient of the expectation into an expectation of the gradient:

$$\nabla_\theta \log \pi(a_t|s_t, \theta) G_t$$

Here $G_t$ is the actual return obtained from time $t$. Multiplying the log-probability of an action by its return effectively "pushes" the policy toward high-reward actions and away from low-reward ones. A critical challenge with policy gradients is **high variance**, which is often mitigated by subtracting a **baseline** $b(s)$ (typically an estimate of the state-value function $V(s)$) from the return: $\nabla J(\theta) \approx \mathbb{E}[\nabla_\theta \log \pi(a|s, \theta)(G_t - b(s))]$.

Unlike value-based methods, policy gradients can learn **stochastic optimal policies**, which are essential for environments with partial observability or adversarial settings (e.g., game theory). They also handle continuous actions naturally by parameterizing the mean and standard deviation of a probability distribution (e.g., a Gaussian), allowing for smooth and differentiable policy updates.

## Applications/Examples

- **Robotics Control:** Policy gradients are the standard for continuous control problems like robotic limb movement, where actions are torque values rather than discrete choices.
- **Natural Language Processing (NLP):** In RL from Human Feedback (RLHF), policy gradients are used to fine-tune large language models like GPT-4 by rewarding the model for generating human-preferred text.
- **Power Grid Management:** Agents use policy gradients to determine continuous-valued adjustments to energy distribution and storage to maintain grid stability.
- **Autonomous Driving:** Many end-to-end driving models use policy-based methods to map raw sensor data directly to steering, acceleration, and braking commands.

## References

- **Sutton, R. S., et al. (1999).** *Policy gradient methods for reinforcement learning with function approximation*. Advances in Neural Information Processing Systems (NIPS). (The paper establishing the Policy Gradient Theorem).
- **Williams, R. J. (1992).** *Simple statistical gradient-following algorithms for connectionist reinforcement learning*. Machine Learning. (Introduces REINFORCE).
- **Sutton, R. S., & Barto, A. G. (2018).** *Reinforcement Learning: An Introduction*. MIT Press. (Chapter 13: Policy Gradient Methods).

