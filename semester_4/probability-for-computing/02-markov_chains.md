## Definition

A **Markov Chain** is a stochastic process that undergoes transitions from one state to another according to certain probabilistic rules. The key property of a Markov chain is the **Markov Property**, which states that the future state depends only on the current state and not on the sequence of events that preceded it.

---

## Transition Matrix

The **transition matrix** PP defines the probabilities of moving from one state to another. It is a square matrix where each element PijPij​ represents the probability of transitioning from state ii to state jj.

### Properties of the Transition Matrix

1. **Rows sum to 1**:  
    Each row of the transition matrix represents a probability distribution, so the sum of the elements in each row must equal 1.
    
2. **Non-negative entries**:  
    All entries in the transition matrix are non-negative.
    

---

# Markov Chain States Explained Simply

## Recurrent vs Transient States

### Recurrent States
**What it means:**  
A state that you're *guaranteed* to come back to again and again.

**Key points:**
- Once you visit it, you'll definitely return
- Like your home - you always come back
- System keeps revisiting infinitely

**Example:**  
In a weather model, "Rainy" is recurrent if rain keeps returning over time.

### Transient States
**What it means:**  
A state you *might not* come back to after leaving.

**Key points:**
- There's a chance you'll never return
- Like a hotel room - you stay once and leave
- System only visits a limited number of times

**Example:**  
"Intern" position is transient if everyone gets promoted eventually.

---

## Periodic vs Aperiodic States

### Periodic States
**What it means:**  
A state that can only be returned to at regular intervals.

**Key points:**
- Returns happen in fixed cycles (every 2, 3, etc. steps)
- Like a bus that comes every hour on the hour
- Has a clear pattern for returns

**Example:**  
In a 2-state cycle (A→B→A→B...), both states have period 2.

### Aperiodic States
**What it means:**  
A state that can be returned to at irregular times.

**Key points:**
- No fixed schedule for returns
- Like a convenience store - you can visit anytime
- More flexible return pattern

**Example:** 
A state with self-loop (can stay or leave) is aperiodic.

---

## Quick Comparison

| Type        | Means...                          | Like...                  | Returns...               |
|-------------|-----------------------------------|--------------------------|--------------------------|
| **Recurrent** | Always comes back               | Your home               | Infinitely often         |
| **Transient** | Might not return                | Hotel room              | Finitely many times      |
| **Periodic**  | Returns at fixed intervals      | Hourly bus              | In regular cycles        |
| **Aperiodic** | Returns anytime                 | 24/7 store              | No fixed pattern         |

---

## Period of a State

The **period** of a state is the greatest common divisor (GCD) of the lengths of all possible trips it would take to return to that state, given that you started at that state.

- If the period is 1, the state is **aperiodic**.
    
- If the period is greater than 1, the state is **periodic**.
    

---

## Aperiodic Markov Chains

A Markov chain is **aperiodic** if all its states are aperiodic (i.e., all states have a period of 1). Aperiodicity is important for ensuring the convergence of the Markov chain to a steady-state distribution.

---

## Example

Consider a Markov chain with two states AA and BB, and the following transition matrix:

Copy

P = [
  [0.7, 0.3],
  [0.4, 0.6]
]

- **Rows sum to 1**:
    
    - Row 1: 0.7 + 0.3 = 1
        
    - Row 2: 0.4 + 0.6 = 1
        
- **Recurrence**:  
    Both states AA and BB are recurrent because the chain will return to each state infinitely often.
    
- **Periodicity**:  
    Both states are aperiodic because the GCD of the lengths of all possible return paths is 1.
    

---

## Key Takeaways

1. **Transition Matrix**:
    
    - Rows sum to 1.
        
    - Represents probabilities of moving between states.
        
2. **State Properties**:
    
    - **Recurrent**: Probability of returning is 1.
        
    - **Transient**: Probability of returning is less than 1.
        
    - **Periodic**: State has a fixed cycle for returning.
        
    - **Aperiodic**: No fixed cycle for returning.
        
3. **Period**:
    
    - The GCD of the lengths of all possible return paths to a state.
        
4. **Aperiodic Chains**:
    
    - All states have a period of 1.
        
    - Important for convergence to a steady-state distribution.
---
## Sojourn Times
- Time when a chain reaches a certain state to when it leaves that state