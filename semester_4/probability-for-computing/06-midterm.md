# Probability & Queuing Theory Cheat Sheet

## Poisson Process & Exponential Distribution

### Formulas
| Concept               | Formula                          | Explanation                                   |
| --------------------- | -------------------------------- | --------------------------------------------- |
| **Poisson PMF**       | `P(N(t)=k) = (e^{-λt}(λt)^k)/k!` | Probability of exactly `k` events in time `t` |
| **Exponential PDF**   | `f(t) = λe^{-λt}`                | Probability density of time between events    |
| **Exponential CDF**   | `F(t) = 1 - e^{-λt}`             | Probability of event occurring by time `t`    |
| **Survival Function** | `S(t) = e^{-λt}`                 | Probability of no events in time `t`          |
| **Memoryless Prop**   | `P(T>t+s \| T>s) = P(T>t)`       | Future events independent of past             |

### Key Properties
- λ = event rate (events per unit time)
- Mean events in time t: `E[N(t)] = λt`
- Mean time between events: `E[T] = 1/λ`
---
## Markov Chains

### Discrete-Time Markov Chains
| Concept               | Formula/Notation           | Explanation                          |
| --------------------- | -------------------------- | ------------------------------------ |
| **Transition Matrix** | `P_ij = P(Xₙ₊₁=j \| Xₙ=i)` | Probability moving from state i to j |
| **n-Step Transition** | `P⁽ⁿ⁾_ij = (Pⁿ)_ij`        | Probability of i→j in n steps        |
| **Recurrent State**   | `∑P⁽ⁿ⁾_ii = ∞`             | State visited infinitely often       |
| **Transient State**   | `∑P⁽ⁿ⁾_ii < ∞`             | State may be left permanently        |

### Continuous-Time Markov Chains
- Governed by rate matrix Q instead of transition matrix P
- Time in state i ~ Exponential(λ_i)
---
## Queuing Theory

### M/M/1 Queue Formulas
| Concept               | Formula                      | Explanation |
|-----------------------|------------------------------|-------------|
| **Traffic Intensity** | `ρ = λ/μ`                    | System utilization (must be < 1) |
| **Avg. in System (L)**| `L = λ/(μ - λ)`              | Expected number in system |
| **Avg. Wait Time (W)**| `W = 1/(μ - λ)`              | Average time in system |
| **Queue Length (L_q)**| `L_q = λ²/(μ(μ - λ))`        | Average number waiting |

### Little's Law
`L = λW`  
Relates average system size (L), arrival rate (λ), and average wait time (W)

### Kendall Notation (x/y/z)
- **x**: Arrival process (`M`=Poisson, `D`=Deterministic, `G`=General)
- **y**: Service process (`M`=Exponential, `D`=Fixed, `G`=General)
- **z**: Number of servers (`1`, `c`, `∞`)

## Gamma Distribution
| Concept       | Formula                          | Explanation |
|---------------|----------------------------------|-------------|
| **PDF**       | `f(t) = (λⁿtⁿ⁻¹e^{-λt})/(n-1)!` | Time until nth event |
| **Mean**      | `E[T] = n/λ`                    | Average waiting time |

## Superposition & Thinning
| Concept         | Formula                          | Explanation |
|-----------------|----------------------------------|-------------|
| **Superposition** | `N₁+N₂ ~ Poisson(λ₁+λ₂)`      | Combining Poisson processes |
| **Thinning**    | `N_A ~ Poisson(pλ)`            | Splitting Poisson process |

## Key Symbols
- **λ (lambda)**: Arrival rate
- **μ (mu)**: Service rate
- **ρ (rho)**: Traffic intensity
- **P_ij**: Transition probability
- **S(t)**: Survival function

## Example Calculations
1. **Poisson Process**:
   - λ = 10/hour, t = 0.05 hours (3 mins)
   - P(1 event): `(e^(-10*0.05)*(10*0.05)^1)/1! = 0.5e^{-0.5}`

2. **M/M/1 Queue**:
   - λ = 3/hour, μ = 4/hour
   - L = 3/(4-3) = 3 customers
   - W = 1/(4-3) = 1 hour
