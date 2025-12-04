# Optimization in Machine Learning

## 1. Introduction
- **Goal**: Find model parameters that minimize/maximize an objective function (e.g., loss function).
- **Key Challenge**: Balance between speed, accuracy, and computational resources.

## 2. Types of Optimization
### 2.1. Convex vs. Non-Convex Optimization
- **Convex**: Single global minimum (e.g., linear regression).
- **Non-Convex**: Multiple local minima (e.g., neural networks).

### 2.2. Constrained vs. Unconstrained
- **Constrained**: Solutions must satisfy conditions (e.g., SVM constraints).
- **Unconstrained**: No restrictions (e.g., ordinary least squares).

---

## 3. Gradient-Based Optimization
### 3.1. Gradient Descent (GD)
- **Update Rule**:  
  \( \theta_{t+1} = \theta_t - \eta \nabla_\theta J(\theta) \)
- **Variants**:
  - **Batch GD**: Uses full dataset (slow, precise).
  - **Stochastic GD (SGD)**: One sample per step (fast, noisy).
  - **Mini-batch GD**: Balances speed/stability (common in DL).

### 3.2. Momentum Methods
- **Classical Momentum**:  
  \( v_{t+1} = \gamma v_t + \eta \nabla_\theta J(\theta) \)  
  \( \theta_{t+1} = \theta_t - v_{t+1} \)
- **Nesterov Momentum**: "Looks ahead" before updating.

### 3.3. Adaptive Methods
- **AdaGrad**: Adapts learning rate per parameter.  
  \( \eta_t = \frac{\eta}{\sqrt{G_t + \epsilon}} \)  
  (Problem: Learning rate decays to zero).
- **RMSProp**: Fixes AdaGrad’s decay by using moving average of \( G_t \).
- **Adam**: Combines Momentum + RMSProp (default choice for many).

---

## 4. Second-Order Methods
- **Newton’s Method**: Uses Hessian matrix for curvature:  
  \( \theta_{t+1} = \theta_t - H^{-1} \nabla_\theta J(\theta) \)
  - Pros: Faster convergence near minima.
  - Cons: Computationally expensive (Hessian calculation/inversion).
- **Quasi-Newton (e.g., L-BFGS)**: Approximates Hessian.

---

## 5. Optimization Challenges
### 5.1. Local Minima & Saddle Points
- **Saddle Points**: More common in high dimensions (gradient ≈ 0 but not minima).
- **Solutions**: Momentum, random restarts, noise injection.

### 5.2. Vanishing/Exploding Gradients
- Common in deep networks.
- **Solutions**: Normalization (BatchNorm), careful initialization (Xavier/He).

### 5.3. Learning Rate Selection
- **Too High**: Divergence.
- **Too Low**: Slow convergence.
- **Solutions**: Learning rate schedules, adaptive methods (Adam).

---

## 6. Hyperparameter Optimization
### 6.1. Methods
- **Grid Search**: Exhaustive but expensive.
- **Random Search**: More efficient than grid search.
- **Bayesian Optimization**: Models loss surface probabilistically.
- **Evolutionary Algorithms**: Genetic algorithms, CMA-ES.

### 6.2. Key Hyperparameters
- Learning rate (\( \eta \)), batch size, momentum (\( \beta \)), network depth/width.

---

## 7. Practical Tips
1. **Normalize Inputs**: Accelerates convergence.
2. **Monitor Loss Curves**: Detect overfitting/underfitting.
3. **Early Stopping**: Prevents overfitting.
4. **Gradient Clipping**: Mitigates exploding gradients (common in RNNs).

---

## 8. References
- **Key Papers**:  
  - Adam (Kingma & Ba, 2015)  
  - RMSProp (Hinton, 2012)