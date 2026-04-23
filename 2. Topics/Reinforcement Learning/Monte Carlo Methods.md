**Tags:** #topic #hub #rl
**Related:** [[Reinforcement Learning]], [[Dynamic Programming for RL]], [[Temporal Difference Learning]], [[Generalized Policy Iteration]]

## Overview
Monte Carlo (MC) methods in Reinforcement Learning are a class of model-free algorithms that learn value functions and optimal policies directly from sampled experience in the form of complete episodes. Unlike Dynamic Programming, MC methods do not require a model of the environment's transition dynamics (i.e., they don't need $p(s', r | s, a)$). Instead, they rely on the fundamental idea of averaging actual returns observed after visiting a state. This makes MC methods particularly suitable for environments where a transition model is unavailable or too complex to define, but where simulation or real-world interaction is possible. The core requirement for MC methods is that the task must be episodic, as updates are only performed once an episode terminates.

## Technical Depth
The theoretical foundation of Monte Carlo methods is the **Law of Large Numbers**: as more returns are sampled for a state, their average converges to the expected value of that state. For a fixed policy $\pi$, the state-value $v_\pi(s)$ is estimated by averaging the returns $G_t$ following all visits to state $s$ across multiple episodes:
$$V(s) \approx \frac{1}{N(s)} \sum_{i=1}^{N(s)} G_{i}(s)$$
There are two primary ways to implement this estimation:
1.  **First-Visit MC:** Only the return following the first visit to state $s$ in an episode is averaged. This estimator is unbiased and converges to $v_\pi(s)$ as $N(s) \to \infty$.
2.  **Every-Visit MC:** Every visit to state $s$ in an episode is treated as a separate sample. While initially biased, it is often more data-efficient and also converges to $v_\pi(s)$ in the limit.

For control (finding the optimal policy), MC methods typically use **Generalized Policy Iteration (GPI)** applied to action-value functions $Q(s,a)$. This is because, in a model-free setting, knowing $V(s)$ is insufficient to determine the best action without a transition model. To ensure that all state-action pairs are explored, MC control often employs the **Exploring Starts** assumption or $\varepsilon$-soft policies. One significant drawback of MC methods is their high variance, as returns can vary wildly between episodes depending on the stochasticity of the environment and the policy. However, because they do not bootstrap (unlike TD learning), they are not biased by initial value estimates.

## Applications/Examples
Monte Carlo methods are effectively used in complex games and simulation-based optimization:
- **Game Playing (Blackjack/Poker):** MC methods are the standard way to learn optimal strategies in games where the state space is manageable but the transition probabilities (e.g., card shuffling) are complex to model explicitly.
- **Monte Carlo Tree Search (MCTS):** Algorithms like AlphaZero use MC simulations to evaluate the strength of different game board positions, combining MC sampling with tree search.
- **Physical Simulations:** In engineering and physics, MC methods help estimate the expected performance or failure rate of systems under various random conditions by running many end-to-end simulations.
- **Epidemiology:** Researchers use Monte Carlo simulations to model the spread of diseases, where each "episode" represents a simulated outbreak under a specific policy (e.g., vaccination or social distancing).

## References
- **Sutton, R. S., & Barto, A. G. (2018).** *Reinforcement Learning: An Introduction*. MIT Press. (Chapter 5).
- **Metropolis, N., & Ulam, S. (1949).** *The Monte Carlo method*. Journal of the American Statistical Association, 44(247), 335-341. (The original conceptual paper).
- **Silver, D., et al. (2017).** *Mastering Chess and Shogi by Self-Play with a General Reinforcement Learning Algorithm*. arXiv. (MCTS and MC evaluation in AlphaZero).

## Knowledge Map

### 1. Foundations
- [[Monte Carlo Prediction]]
- [[First-Visit vs Every-Visit MC]]

### 2. Control
- [[Monte Carlo Control]]
- [[Exploring Starts]]
- [[On-Policy MC Control]]
- [[Off-Policy MC Control]]

### 3. Off-Policy Methods
- [[Importance Sampling]]

> [!question]- Common Exam Questions
> - What is the difference between First-Visit and Every-Visit MC, and which has stronger theoretical guarantees?
> - Why must MC methods estimate action-value functions rather than state-value functions in the model-free setting?
> - What are the two assumptions required for MC to converge to the optimal policy, and how does each get relaxed in practice?
> - How does the Importance Sampling ratio enable off-policy learning, and what is the difference between ordinary and weighted Importance Sampling?
