# Poisson Process: Comprehensive Guide

## 1. Definition and Key Properties
A **Poisson Process** is a continuous-time counting process that models random events occurring independently at a constant average rate.

### Formal Definition
A process $\{N(t), t \geq 0\}$ is a Poisson process with rate $\lambda > 0$ if:
1. $N(0) = 0$
2. Independent increments
3. Stationary increments
4. For small $\Delta t$:
   - $P(N(t+\Delta t) - N(t) = 1) \approx \lambda\Delta t$
   - $P(N(t+\Delta t) - N(t) \geq 2) \approx 0$

### Key Characteristics
- **Counting Process**: $N(t) = \#$ events in $[0,t]$
- **Rate Parameter**: $\lambda$ (average events per unit time)
- **Memoryless**: Future events depend only on current state

---

## 2. Types of Poisson Processes

### Homogeneous Poisson Process
- Constant rate $\lambda$
- Probability mass function:
  $$P(N(t) = k) = \frac{e^{-\lambda t}(\lambda t)^k}{k!}, \quad k = 0,1,2,...$$

### Non-Homogeneous Poisson Process
- Time-varying rate $\lambda(t)$
- Cumulative intensity:
  $$\Lambda(t) = \int_0^t \lambda(\tau) d\tau$$
- PMF:
  $$P(N(t) = k) = \frac{e^{-\Lambda(t)}(\Lambda(t))^k}{k!}$$

### Compound Poisson Process
- Each event has random magnitude $X_i$:
  $$S(t) = \sum_{i=1}^{N(t)} X_i$$
- Mean and variance:
  $$E[S(t)] = \lambda t E[X], \quad Var(S(t)) = \lambda t E[X^2]$$

---

## 3. Formulas and Properties

### Basic Formulas
| Property | Formula |
|----------|---------|
| Mean events in time t | $E[N(t)] = \lambda t$ |
| Variance | $Var(N(t)) = \lambda t$ |
| Probability of 0 events | $P(N(t)=0) = e^{-\lambda t}$ |
| Probability of ≥1 event | $P(N(t)\geq1) = 1 - e^{-\lambda t}$ |

### Moment Generating Function
$$M_{N(t)}(\theta) = E[e^{\theta N(t)}] = \exp\{\lambda t(e^\theta - 1)\}$$

---

## 4. Interarrival and Waiting Times

### Interarrival Times ($T_i$)
- Time between $(i-1)$th and $i$th events
- Exponentially distributed:
  $$P(T_i \leq t) = 1 - e^{-\lambda t}, \quad t \geq 0$$
- Mean interarrival time: $E[T_i] = 1/\lambda$

### Waiting Time for nth Event ($S_n$)
- Gamma distributed:
  $$f_{S_n}(t) = \frac{\lambda^n t^{n-1} e^{-\lambda t}}{(n-1)!}, \quad t \geq 0$$
- Mean waiting time: $E[S_n] = n/\lambda$

---

## 5. Superposition and Thinning

### Superposition
Combining independent Poisson processes:
$$N_1(t) \sim Poisson(\lambda_1), N_2(t) \sim Poisson(\lambda_2) \Rightarrow N_1(t) + N_2(t) \sim Poisson(\lambda_1 + \lambda_2)$$

### Thinning
Splitting a Poisson process with probability $p$:
$$
N(t) \sim Poisson(\lambda) \Rightarrow 
\begin{cases}
N_1(t) \sim Poisson(p\lambda) \\
N_2(t) \sim Poisson((1-p)\lambda)
\end{cases}
$$

---

## 6. Non-Homogeneous Poisson Process

### Key Properties
- Rate function $\lambda(t)$ varies with time
- Expected events by time $t$:
  $$\Lambda(t) = \int_0^t \lambda(\tau) d\tau$$
- Transformation to homogeneous process:
  $$N(t) = N_h(\Lambda(t))$$
  where $N_h$ is a standard Poisson process

---

## 7. Compound Poisson Process

### Definition
$$S(t) = \sum_{i=1}^{N(t)} X_i$$
where $\{X_i\}$ are i.i.d. random variables independent of $N(t)$

### Moments
| Moment | Formula |
|--------|---------|
| Mean | $E[S(t)] = \lambda t E[X]$ |
| Variance | $Var(S(t)) = \lambda t E[X^2]$ |
| MGF | $M_{S(t)}(\theta) = \exp\{\lambda t(M_X(\theta) - 1)\}$ |

---

## 8. Examples

### Example 1: Call Center
- Calls arrive at $\lambda = 10$/hour
- Probability of exactly 5 calls in 30 minutes:
  $$P(N(0.5)=5) = \frac{e^{-5}(5)^5}{5!} \approx 0.1755$$

### Example 2: Server Requests
- Requests arrive at $\lambda = 1000$/minute
- Probability of no requests in 1ms:
  $$P(N(1/60000)=0) = e^{-1000/60000} \approx 0.9835$$

---

## 9. Applications

### Common Use Cases
1. **Telecommunications**: Modeling call arrivals
2. **Finance**: Jumps in stock prices
3. **Reliability**: Machine failure occurrences
4. **Biology**: Mutation occurrences
5. **Queueing Theory**: Customer arrivals

### Real-World Examples
- Web server requests
- Insurance claim filings
- Radioactive decay events
- Traffic flow modeling

---

## 10. Poisson Process vs Related Distributions

| Distribution | Models | Relationship to Poisson |
|--------------|--------|-------------------------|
| **Exponential** | Interarrival times | $T_i \sim Exp(\lambda)$ for Poisson |
| **Gamma** | Waiting time for n events | $S_n \sim Gamma(n, \lambda)$ |
| **Binomial** | Successes in n trials | $Bin(n,p) \approx Poisson(np)$ for large n |
| **Normal** | Sum of many events | $N(t) \approx N(\lambda t, \lambda t)$ for large $\lambda t$ |

---

## Summary Cheatsheet

| Concept            | Formula                                    |
| ------------------ | ------------------------------------------ |
| PMF                | $$P(N(t)=k) = \frac{e^{-\lambda t}(\lambda t)^k}{k!}$$ |
| Interarrival Times | $$T_i \sim Exp(\lambda)$$                  |
| Waiting Time       | $$S_n \sim Gamma(n, \lambda)$$             |
| Superposition      | $$N_1 + N_2 \sim Poisson(\lambda_1 + \lambda_2)$$ |
| Thinning           | $$N_A \sim Poisson(p\lambda)$$             |
| Compound Process   | $$S(t) = \sum_{i=1}^{N(t)} X_i$$          |