**Tags:** #concept #rl
**Related:** [[Markov Chain]], [[Graphs, Search, and MDPs]], [[Bellman Equation]], [[RL Policy]]

## Overview

A Markov Decision Process (MDP) is a mathematical framework for modeling sequential decision-making in environments where outcomes are partly random and partly under the control of a decision-maker. As the standard formal model for reinforcement learning, it bridges the gap between pure state transitions (Markov Chains) and goal-oriented optimization. The MDP provides a rigorous language to describe how an agent interacts with its environment to achieve long-term objectives, formalizing concepts such as state, action, reward, and transition dynamics.

## Technical Depth

A finite MDP is formally defined by a quintuple $(\mathcal{S}, \mathcal{A}, p, \mathcal{R}, \gamma)$. The set $\mathcal{S}$ represents the state space, while $\mathcal{A}(s)$ denotes the finite set of actions available from state $s$. The **dynamics function** $p(s',r \mid s,a) \doteq \text{Pr}\{S_t=s', R_t=r \mid S_{t-1}=s, A_{t-1}=a\}$ is the core engine of the MDP, defining the probability of transitioning to state $s'$ and receiving reward $r$ given the previous state $s$ and action $a$. This function must satisfy the **Markov Property**, which asserts that the future state depends only on the current state and action, and not on the history of previous events.

$$p(s',r \mid s,a) = \text{Pr}\{S_t=s', R_t=r \mid S_{t-1}=s, A_{t-1}=a\}$$

From the dynamics function, other useful quantities are derived, such as the state-transition probability $p(s' \mid s,a) = \sum_{r \in \mathcal{R}} p(s',r \mid s,a)$ and the expected reward $r(s,a) = \sum_{r \in \mathcal{R}} r \sum_{s' \in \mathcal{S}} p(s',r \mid s,a)$. The agent's behavior is guided by a **policy** $\pi(a|s)$, which is a mapping from states to probabilities of selecting each action. The goal of solving an MDP is to find an optimal policy $\pi_*$ that maximizes the expected discounted return $G_t = \sum_{k=0}^{\infty} \gamma^k R_{t+k+1}$, where $\gamma \in [0, 1]$ handles the trade-off between immediate and future rewards.

## Applications/Examples

- **Inventory Management:** A warehouse agent decides how much stock to order each day, balancing storage costs, ordering fees, and the risk of stockouts given uncertain demand.
- **Robot Navigation:** An autonomous vehicle determines its movement actions based on sensor readings, where the state space includes its coordinates and velocity, and rewards are given for reaching a destination safely.
- **Clinical Trials:** MDPs are used to determine sequential treatment strategies (Dynamic Treatment Regimes) for patients based on their changing health status over time.
- **Resource Allocation:** In cloud computing, MDPs help in dynamically assigning virtual machines to physical servers to optimize power consumption and service-level agreements.

## References

- **Sutton, R. S., & Barto, A. G. (2018).** *Reinforcement Learning: An Introduction*. MIT Press. (Chapter 3: Finite Markov Decision Processes).
- **Puterman, M. L. (1994).** *Markov Decision Processes: Discrete Stochastic Dynamic Programming*. John Wiley & Sons. (The definitive graduate-level text).
- **Bellman, R. (1957).** *A Markovian Decision Process*. Journal of Mathematics and Mechanics.

