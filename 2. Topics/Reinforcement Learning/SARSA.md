**Tags:** #concept #rl
**Related:** [[Temporal Difference Learning]], [[Q-Learning]], [[Expected SARSA]], [[RL Policy]]

## Overview
SARSA (State-Action-Reward-State-Action) is an on-policy temporal difference (TD) control algorithm used in reinforcement learning. As an on-policy method, SARSA learns the action-value function $q_\pi(s,a)$ based on the actions actually taken by the agent according to its current (often exploratory) policy $\pi$. This distinguishes it from off-policy methods like Q-learning, which learn the optimal value function $q_*(s,a)$ regardless of the agent's behavior. Because SARSA incorporates the cost of exploration into its value estimates, it is often more conservative and safer than Q-learning during the learning process, making it particularly valuable in real-world scenarios where accidental negative rewards carry a significant cost.

## Technical Depth
The name SARSA describes the sequence of events that trigger an update: the agent starts in state $S_t$, takes action $A_t$, receives reward $R_{t+1}$, transitions to state $S_{t+1}$, and then selects the *next* action $A_{t+1}$ using its current policy. The update rule for SARSA is:
$$Q(S_t, A_t) \leftarrow Q(S_t, A_t) + \alpha [R_{t+1} + \gamma Q(S_{t+1}, A_{t+1}) - Q(S_t, A_t)]$$
where $\alpha$ is the learning rate and $\gamma$ is the discount factor.

In SARSA, the target for the update is $R_{t+1} + \gamma Q(S_{t+1}, A_{t+1})$, which depends on the actual action $A_{t+1}$ chosen by the policy. If the agent is using an $\varepsilon$-greedy policy, the value of $Q(S_t, A_t)$ will reflect the fact that the agent might take a suboptimal random action in the next step. This property is why SARSA is considered "on-policy." For example, in a "Cliff Walking" task, SARSA will learn to stay far away from the cliff edge because it accounts for the probability of accidentally falling off due to $\varepsilon$-greedy exploration. In contrast, Q-learning would learn the path right along the edge, assuming it will always take the optimal action in the future. SARSA converges to the optimal policy $\pi_*$ and optimal value function $q_*$ as long as all state-action pairs are visited infinitely often and the policy becomes greedy in the limit (GLIE).

## Applications/Examples
SARSA is preferred in applications where safety and online performance are critical:
- **Autonomous Driving:** SARSA is used to train lane-keeping and collision-avoidance systems where exploratory "mistakes" (like abrupt steering) must be accounted for in the value function to ensure the agent learns a robust and safe strategy.
- **Industrial Control:** In chemical plants or power grids, SARSA helps optimize operations by learning values that account for the potential instability caused by exploratory adjustments to system parameters.
- **Personalized Recommendations:** Online platforms use SARSA to learn user preferences while exploring new items, ensuring that the "cost" of showing a potentially irrelevant item is factored into the long-term engagement model.
- **Robotics:** SARSA is used in robot gait learning where falling over is costly; the agent learns a stable walk that is robust to the stochasticity inherent in its own motor babbling.

## References
- **Sutton, R. S., & Barto, A. G. (2018).** *Reinforcement Learning: An Introduction*. MIT Press. (Chapter 6.4).
- **Rummery, G. A., & Niranjan, M. (1994).** *On-line Q-learning using connectionist systems*. University of Cambridge, Department of Engineering. (Original introduction of SARSA).
- **Singh, S., et al. (2000).** *Convergence Results for Single-Step On-Policy Reinforcement-Learning Algorithms*. Machine Learning, 38, 287-308.

