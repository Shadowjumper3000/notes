## 1. Introduction to Markov Chains

A **Markov chain** is a stochastic process that undergoes transitions from one state to another within a finite or countable number of possible states. It satisfies the **Markov property**:

The future state depends only on the present state, not on the sequence of events that preceded it.

### Key Components
- **State space**: A finite or countable set  
  $$ S = \{s_1, s_2, \dots, s_n\} $$
- **Transition matrix**:  
  $$ P = [p_{ij}] \quad \text{where} \quad p_{ij} = P(X_{t+1} = s_j \mid X_t = s_i) $$

### Properties
- **Memorylessness**:  
  $$ P(X_{t+1} = s_j \mid X_t = s_i, X_{t-1} = s_k, \dots, X_0 = s_0) = P(X_{t+1} = s_j \mid X_t = s_i) $$

- **Row-stochastic matrix** (each row sums to 1):  
  $$ \sum_j p_{ij} = 1 \quad \forall i $$

### Example

For states $A$ and $B$, the transition matrix might be:

$$
P = \begin{bmatrix}
0.7 & 0.3 \\
0.4 & 0.6
\end{bmatrix}
$$

This means from state $A$, the system transitions to $A$ with 70% probability and to $B$ with 30%.

### Applications
- Weather modeling
- Web navigation (e.g., PageRank)
- Genetics
- Game theory


## 2. Markov Chains and Stationary Distributions

A **stationary distribution** is a probability distribution over the states of a Markov chain that remains unchanged as the system evolves over time. If the Markov chain starts in the stationary distribution, it stays in that distribution at every step.

### Definition

A row vector $\pi$ is a stationary distribution for a transition matrix $P$ if:

$$
\pi P = \pi
$$

and

$$
\sum_i \pi_i = 1, \quad \pi_i \geq 0 \ \forall i
$$

This means that $\pi$ is a **left eigenvector** of $P$ corresponding to eigenvalue 1.

### Conditions for Existence and Uniqueness

A Markov chain has a **unique stationary distribution** if it is:

- **Irreducible**: It is possible to get from any state to any other state (not necessarily in one step).
- **Aperiodic**: The system does not return to a state in a fixed cycle.
- **Positive recurrent**: The expected return time to any state is finite.

Under these conditions, the Markov chain is **ergodic**, and the distribution of states converges to the stationary distribution regardless of the initial state:

$$
\lim_{t \to \infty} P^t(x_0, \cdot) = \pi
$$

### Example

Given transition matrix:

$$
P = \begin{bmatrix}
0.5 & 0.5 \\
0.2 & 0.8
\end{bmatrix}
$$

Solve for $\pi$:

$$
\pi = [\pi_1, \pi_2] \quad \text{such that} \quad \pi P = \pi
$$

This yields a system of equations:

$$
\begin{cases}
0.5 \pi_1 + 0.2 \pi_2 = \pi_1 \\
0.5 \pi_1 + 0.8 \pi_2 = \pi_2 \\
\pi_1 + \pi_2 = 1
\end{cases}
$$

Solving gives:

$$
\pi = \left[\frac{2}{7}, \frac{5}{7}\right]
$$

### Significance

Stationary distributions are used to:

- Understand long-run behavior
- Analyze equilibrium conditions
- Power algorithms like Google's PageRank


## 3. The Exponential Distribution

The **exponential distribution** is a continuous probability distribution commonly used to model the time between independent events that occur at a constant average rate. It is a key component of the Poisson process.

### Probability Density Function (PDF)

For a non-negative random variable $T$, the exponential distribution with rate parameter $\lambda > 0$ is defined by:

$$
f(t) = \lambda e^{-\lambda t}, \quad t \geq 0
$$

### Cumulative Distribution Function (CDF)

The probability that an event occurs by time $t$ is:

$$
F(t) = P(T \leq t) = 1 - e^{-\lambda t}
$$

### Memoryless Property

The exponential distribution is **memoryless**, meaning:

$$
P(T > s + t \mid T > s) = P(T > t)
$$

This is a unique property among continuous distributions and implies the future waiting time is independent of the past.

### Mean and Variance

- **Expected value**:
  $$
  \mathbb{E}[T] = \frac{1}{\lambda}
  $$

- **Variance**:
  $$
  \text{Var}(T) = \frac{1}{\lambda^2}
  $$

### Applications

- Time between arrivals in a Poisson process
- Reliability of systems (e.g., lifetime of electronic components)
- Modeling service times in queuing systems
- Survival analysis

### Example

If $\lambda = 2$, the PDF is:

$$
f(t) = 2 e^{-2t}
$$

The mean time between events is:

$$
\mathbb{E}[T] = \frac{1}{2} = 0.5
$$

## 4. The Poisson Process

The **Poisson process** is a fundamental stochastic process used to model random events that occur independently and uniformly over time. It is characterized by a single parameter: the **rate** $\lambda > 0$, which represents the average number of events per unit time.

### Key Properties

1. **Independent increments**: The number of events in disjoint time intervals are independent.
2. **Stationary increments**: The probability of a certain number of events occurring in a time interval depends only on the length of the interval, not its location on the timeline.
3. **No simultaneous events**: The probability of more than one event occurring in an infinitesimally small time interval is negligible.

### Interarrival Times

Let $T_i$ be the time between the $(i-1)$-th and $i$-th event. Then:

$$
T_i \sim \text{Exponential}(\lambda)
$$

The times between events are **independent and identically distributed (i.i.d.)** exponential random variables.

### Counting Process

Let $N(t)$ denote the number of events up to time $t$. Then:

$$
P(N(t) = k) = \frac{(\lambda t)^k e^{-\lambda t}}{k!}, \quad k = 0, 1, 2, \dots
$$

This is the **Poisson distribution** with mean $\lambda t$.

### Mean and Variance

- **Expected number of events by time $t$**:
  $$
  \mathbb{E}[N(t)] = \lambda t
  $$

- **Variance**:
  $$
  \text{Var}(N(t)) = \lambda t
  $$

### Applications

- Modeling arrival of customers, emails, or calls
- Counting radioactive decay events
- Network traffic modeling
- Reliability engineering

### Example

If $\lambda = 3$ events per hour:

- The probability of observing exactly 4 events in 2 hours is:

$$
P(N(2) = 4) = \frac{(3 \cdot 2)^4 e^{-3 \cdot 2}}{4!} = \frac{6^4 e^{-6}}{24}
$$


## 5. Queuing Theory

**Queuing theory** is the mathematical study of waiting lines, or queues. It uses stochastic processes—often based on Markov chains and Poisson processes—to model and analyze systems where entities wait for service.

### Basic Components of a Queue

- **Arrival process**: Describes how entities arrive (commonly modeled as a Poisson process).
- **Service mechanism**: How entities are served (typically with exponential service times).
- **Number of servers**: Single-server or multi-server systems.
- **Queue discipline**: Rules for service order (e.g., FIFO, LIFO).
- **System capacity**: Maximum number of entities in the system.

### Kendall’s Notation

A queue is described as **A/S/c**, where:
- **A** = Arrival process
- **S** = Service time distribution
- **c** = Number of servers

Common models:
- **M/M/1**: Poisson arrivals, exponential service times, 1 server
- **M/G/1**: Poisson arrivals, general service time, 1 server
- **G/M/1**: General arrival, exponential service time, 1 server

### M/M/1 Queue Model

Assume:
- Arrival rate $\lambda$
- Service rate $\mu$
- Traffic intensity $\rho = \frac{\lambda}{\mu} < 1$

#### Steady-State Probabilities

The probability the system has $n$ customers:

$$
P_n = (1 - \rho)\rho^n, \quad n = 0, 1, 2, \dots
$$

#### Performance Metrics

- **Expected number in the system**:
  $$
  \mathbb{E}[N] = \frac{\rho}{1 - \rho}
  $$

- **Expected number in the queue**:
  $$
  \mathbb{E}[N_q] = \frac{\rho^2}{1 - \rho}
  $$

- **Expected time in the system**:
  $$
  \mathbb{E}[T] = \frac{1}{\mu - \lambda}
  $$

- **Expected time in the queue**:
  $$
  \mathbb{E}[T_q] = \frac{\lambda}{\mu(\mu - \lambda)}
  $$

### Applications

- Call centers
- Computer networks
- Manufacturing systems
- Hospital patient flow
- Traffic engineering

### Example

For an M/M/1 queue with $\lambda = 3$ and $\mu = 5$:

- Traffic intensity: $\rho = \frac{3}{5} = 0.6$
- Expected number in the system:  
  $$
  \mathbb{E}[N] = \frac{0.6}{1 - 0.6} = 1.5
  $$
- Expected wait time:  
  $$
  \mathbb{E}[T] = \frac{1}{5 - 3} = 0.5 \text{ units of time}
  $$


## 6. Introduction to Bayesian networks

Bayesian networks (also called belief networks or Bayes nets) are **probabilistic graphical models** that represent a collection of random variables and their **conditional dependencies** through a **directed acyclic graph (DAG)**. Each node in the graph corresponds to a variable, and edges encode direct dependencies between variables.

### Key components:

- **Nodes:** Represent random variables, which can be discrete or continuous.
- **Edges:** Directed arrows indicating conditional dependencies; an edge from node \(A\) to node \(B\) implies that \(A\) has a direct influence on \(B\).
- **Conditional Probability Tables (CPTs):** Each node has an associated CPT that quantifies the effect of its parents on its own probability distribution.

### Intuition and purpose

Bayesian networks provide a compact way to model complex joint distributions by exploiting **conditional independencies** between variables. Instead of specifying a full joint probability distribution over all variables (which grows exponentially with the number of variables), the network factorizes the joint distribution into a product of local conditional probabilities.

### Mathematical formulation

Given a set of variables \(X = \{X_1, X_2, \ldots, X_n\}\), the joint probability distribution encoded by a Bayesian network factorizes as:

$$
P(X_1, X_2, \ldots, X_n) = \prod_{i=1}^n P\left(X_i \mid \text{Parents}(X_i)\right)
$$

where \(\text{Parents}(X_i)\) denotes the set of direct predecessor nodes of \(X_i\) in the DAG.

### Benefits of Bayesian networks

- **Compactness:** Efficient representation of high-dimensional distributions by leveraging conditional independence.
- **Interpretability:** Graph structure provides a clear visualization of dependencies and causal relationships.
- **Inference:** Supports various probabilistic queries, such as computing marginal and conditional probabilities.
- **Learning:** Parameters and sometimes even structure can be learned from data using statistical methods.

### Inference in Bayesian networks

Typical inference tasks include:

- **Marginalization:** Computing the probability of a subset of variables by summing/integrating out others.
- **Conditioning:** Updating beliefs given observed evidence.
- **Most probable explanation (MPE):** Finding the most likely assignment to unobserved variables given evidence.

Various algorithms exist for inference, such as variable elimination, belief propagation, and sampling methods.

---

Bayesian networks form the foundation for many applications in machine learning, artificial intelligence, and decision support systems due to their ability to model uncertainty and complex dependencies in a structured way.


## 7. Conditional independence

**Conditional independence** is a key concept in probability theory and Bayesian networks. It describes a situation where two random variables are independent **given** the knowledge of a third variable. Formally, variables \(X\) and \(Y\) are conditionally independent given \(Z\) if knowing \(Z\) renders \(X\) and \(Y\) independent of each other.

### Formal definition

Two variables \(X\) and \(Y\) are **conditionally independent** given a variable \(Z\) if and only if:

$$
P(X, Y \mid Z) = P(X \mid Z) \, P(Y \mid Z)
$$

This implies that once we know \(Z\), knowing \(Y\) provides no additional information about \(X\), and vice versa.

### Notation

Conditional independence is often denoted as:

$$
X \perp\!\!\!\perp Y \mid Z
$$

meaning "X is independent of Y given Z."

### Importance in Bayesian networks

Conditional independence is fundamental to the structure and efficiency of Bayesian networks:

- It allows the **factorization** of the joint probability distribution into simpler terms (see section 6).
- It reduces the number of parameters needed to describe the network.
- It simplifies inference by breaking down complex dependencies into smaller, manageable components.

### Examples

1. **Medical diagnosis:** Suppose \(X\) = presence of a disease, \(Y\) = symptom A, and \(Z\) = test result. Once the test result \(Z\) is known, the symptom \(Y\) may provide no extra information about the disease \(X\), meaning \(X\) and \(Y\) are conditionally independent given \(Z\).

2. **Bayesian network structure:** If a node \(X\) is conditionally independent of all other non-descendants given its parents, this property enables efficient representation and computation.

### Relation to d-separation

In Bayesian networks, conditional independence can be determined graphically using **d-separation**, a criterion that checks whether a set of nodes blocks all paths between two variables, thereby rendering them conditionally independent given that set.

---

By exploiting conditional independence, Bayesian networks efficiently capture the probabilistic relationships among variables without enumerating the entire joint distribution.


## 8. D-separation

**D-separation** (directional separation) is a graphical criterion used in Bayesian networks to determine conditional independence relationships between sets of variables. It provides a method to read off from the network structure whether a set of variables \(X\) is conditionally independent of another set \(Y\) given a third set \(Z\).

### Purpose

D-separation helps interpret and analyze the **probabilistic dependencies** encoded by the directed acyclic graph (DAG) of a Bayesian network without explicitly referring to probability distributions.

### Definition

Given three disjoint sets of nodes \(X\), \(Y\), and \(Z\) in a Bayesian network, \(X\) and \(Y\) are **d-separated** by \(Z\) if all paths between any node in \(X\) and any node in \(Y\) are **blocked** by \(Z\).

### What Does It Mean for a Path to Be "Blocked"?

A path between two nodes is **blocked** by a set of observed variables \(Z\) if at least one of the following conditions holds **anywhere along the path**:

---

#### 1. **Chain Structure**

$$
A \rightarrow B \rightarrow C \quad \text{or} \quad A \leftarrow B \leftarrow C
$$

The path is **blocked** if the **middle node \(B\)** is in the conditioning set:

$$
B \in Z
$$

---

#### 2. **Fork Structure**

$$
A \leftarrow B \rightarrow C
$$

This is also **blocked** if the **middle node \(B\)** is in the conditioning set:

$$
B \in Z
$$

---

#### 3. **Collider Structure**

$$
A \rightarrow B \leftarrow C
$$

This path is **blocked** if the **middle node \(B\)** is **not in \(Z\)** and **no descendant of \(B\)** is in \(Z$:

$$
B \notin Z \quad \text{and} \quad \text{Descendants}(B) \cap Z = \emptyset
$$

If either \(B \in Z\) or a **descendant** of \(B\) is in \(Z\), the collider **activates** the path (i.e., **unblocks** it).

---


### Summary in simpler terms:

- Conditioning on a node in a **chain** or **fork** blocks the path.
- Conditioning on a **collider** node or its descendants *unblocks* the path.
- If all paths between \(X\) and \(Y\) are blocked by \(Z\), then \(X\) and \(Y\) are d-separated by \(Z\).

### Implication

If \(X\) and \(Y\) are d-separated by \(Z\) in the graph, then they are conditionally independent given \(Z\):

$$
X \perp\!\!\!\perp Y \mid Z
$$

### Why is d-separation important?

- It allows us to **read off** conditional independencies directly from the graph.
- It forms the theoretical basis for learning and reasoning with Bayesian networks.
- It aids in designing efficient inference algorithms by identifying irrelevant variables given observed evidence.

---

D-separation bridges the gap between the graphical structure of Bayesian networks and the underlying probabilistic dependencies, making it an essential tool for understanding and working with these models.


## 9. Inference and sampling

**Inference** in probabilistic models refers to the process of computing **marginal** or **conditional probabilities** of certain variables given observed evidence. In Bayesian networks, inference enables answering queries such as "What is the probability of event \(A\) given evidence \(E\)?"

### Types of inference tasks

- **Marginalization:** Computing the probability distribution of a subset of variables by summing or integrating out the remaining variables.
- **Conditional inference:** Computing probabilities conditioned on observed evidence.
- **Most probable explanation (MPE):** Finding the most likely assignment of variables given evidence.

### Exact inference methods

Exact inference algorithms compute probabilities without approximation, but their complexity often grows exponentially with the network size.

- **Variable elimination:** Systematically eliminates variables by summing over them, exploiting the factorization of the network.
- **Belief propagation (message passing):** Efficient in tree-structured networks; propagates local messages to compute marginals.
- **Junction tree algorithm:** Converts the network into a tree structure of cliques to enable efficient inference.

### Approximate inference methods

When exact inference is computationally infeasible (especially in large or densely connected networks), approximate methods are employed.

- **Monte Carlo sampling:** Uses random samples to estimate probability distributions.
- **Rejection sampling:** Samples from the prior distribution, rejecting samples inconsistent with evidence.
- **Likelihood weighting:** Samples weighted by the likelihood of evidence to improve efficiency.
- **Gibbs sampling:** A Markov Chain Monte Carlo (MCMC) method that samples each variable conditioned on the current values of all others iteratively.

### Example: Gibbs sampling

In Gibbs sampling, each variable \(X_i\) is sampled from its conditional distribution given all other variables:

$$
X_i^{(t+1)} \sim P\left(X_i \mid X_1^{(t+1)}, \ldots, X_{i-1}^{(t+1)}, X_{i+1}^{(t)}, \ldots, X_n^{(t)}\right)
$$

By iterating this process, samples approximate the joint distribution, allowing estimation of marginals or other queries.

---

Inference and sampling form the computational backbone of Bayesian networks, enabling them to answer probabilistic queries and make predictions in complex uncertain environments.


## 10. Naive Bayes model

The **Naive Bayes** model is a simple yet powerful probabilistic classifier based on **Bayes’ theorem**, with the key assumption that all features are **conditionally independent** given the class label. This "naive" assumption dramatically simplifies the computation of the joint likelihood.

### Model structure

Given a class variable \(C\) and feature variables \(X_1, X_2, \ldots, X_n\), the Naive Bayes model assumes:

$$
P(X_1, X_2, \ldots, X_n \mid C) = \prod_{i=1}^n P(X_i \mid C)
$$

This means each feature \(X_i\) is independent of every other feature given the class \(C\).

### Classification rule

Using Bayes’ theorem, the posterior probability of class \(C = c\) given features \(\mathbf{X} = (x_1, x_2, \ldots, x_n)\) is:

$$
P(C = c \mid \mathbf{X}) = \frac{P(C = c) \prod_{i=1}^n P(X_i = x_i \mid C = c)}{P(\mathbf{X})}
$$

Since \(P(\mathbf{X})\) is constant across classes, classification is typically done by choosing the class with the highest **posterior probability**:

$$
\hat{c} = \arg\max_c \, P(C = c) \prod_{i=1}^n P(X_i = x_i \mid C = c)
$$

### Advantages

- **Simplicity:** Easy to implement and computationally efficient.
- **Scalability:** Handles high-dimensional data well due to factorization.
- **Robustness:** Performs surprisingly well even when independence assumptions are violated.
- **Interpretability:** Provides probabilistic outputs useful for decision-making.

### Common applications

- **Text classification:** Spam filtering, sentiment analysis, document categorization.
- **Medical diagnosis:** Predicting diseases from symptoms.
- **Recommendation systems:** Classifying user preferences.

---

Despite its simplicity and strong independence assumptions, the Naive Bayes model remains a popular baseline classifier due to its efficiency and competitive performance on many real-world tasks.

