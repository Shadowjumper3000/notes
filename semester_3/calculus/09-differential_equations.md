# Differential Equations

## Introduction

A **differential equation** relates a function to its derivatives.

### Classification

**Order:** Highest derivative present
- First-order: involves $\frac{dy}{dx}$
- Second-order: involves $\frac{d^2y}{dx^2}$

**Linearity:**
- **Linear:** No products or powers of $y$ or its derivatives
- **Nonlinear:** Contains products, powers, or nonlinear functions of $y$

---

## First-Order Differential Equations

### Separable Equations

Form: $\frac{dy}{dx} = g(x)h(y)$

**Solution method:**
1. Separate variables: $\frac{dy}{h(y)} = g(x)\,dx$
2. Integrate both sides
3. Solve for $y$ if possible

**Example:**
$$
\frac{dy}{dx} = xy
$$

Separate: $\frac{dy}{y} = x\,dx$

Integrate: $\ln|y| = \frac{x^2}{2} + C$

Solution: $y = Ae^{x^2/2}$ where $A = \pm e^C$

---

### Linear First-Order Equations

Form: $\frac{dy}{dx} + P(x)y = Q(x)$

**Solution method:**
1. Find integrating factor: $\mu(x) = e^{\int P(x)\,dx}$
2. Multiply equation by $\mu(x)$
3. Left side becomes $\frac{d}{dx}[\mu(x)y]$
4. Integrate: $\mu(x)y = \int \mu(x)Q(x)\,dx + C$

**Example:**
$$
\frac{dy}{dx} + 2xy = x
$$

Integrating factor: $\mu = e^{\int 2x\,dx} = e^{x^2}$

Multiply: $e^{x^2}\frac{dy}{dx} + 2xe^{x^2}y = xe^{x^2}$

$$
\frac{d}{dx}[e^{x^2}y] = xe^{x^2}
$$

Integrate: $e^{x^2}y = \frac{1}{2}e^{x^2} + C$

Solution: $y = \frac{1}{2} + Ce^{-x^2}$

---

### Exact Equations

Form: $M(x, y)\,dx + N(x, y)\,dy = 0$

**Test for exactness:**
$$
\frac{\partial M}{\partial y} = \frac{\partial N}{\partial x}
$$

If exact, there exists $F(x, y)$ such that:
$$
\frac{\partial F}{\partial x} = M, \quad \frac{\partial F}{\partial y} = N
$$

**Solution:** $F(x, y) = C$

**Method:**
1. Integrate $M$ with respect to $x$: $F = \int M\,dx + g(y)$
2. Differentiate with respect to $y$ and set equal to $N$
3. Solve for $g(y)$

---

### Homogeneous Equations

Form: $\frac{dy}{dx} = f\left(\frac{y}{x}\right)$

**Solution method:**
1. Substitute $v = \frac{y}{x}$, so $y = vx$ and $\frac{dy}{dx} = v + x\frac{dv}{dx}$
2. Equation becomes separable in $v$ and $x$

---

### Bernoulli Equations

Form: $\frac{dy}{dx} + P(x)y = Q(x)y^n$

**Solution method:**
1. Divide by $y^n$: $y^{-n}\frac{dy}{dx} + P(x)y^{1-n} = Q(x)$
2. Substitute $v = y^{1-n}$
3. Resulting equation is linear in $v$

---

## Applications of First-Order DEs

### Exponential Growth/Decay

$$
\frac{dy}{dt} = ky
$$

**Solution:** $y = y_0 e^{kt}$

- $k > 0$: Growth (population, compound interest)
- $k < 0$: Decay (radioactive decay, cooling)

### Newton's Law of Cooling

$$
\frac{dT}{dt} = -k(T - T_{\text{ambient}})
$$

**Solution:** $T(t) = T_{\text{ambient}} + (T_0 - T_{\text{ambient}})e^{-kt}$

### Logistic Growth

$$
\frac{dP}{dt} = kP\left(1 - \frac{P}{K}\right)
$$

where $K$ is carrying capacity.

**Solution:** $P(t) = \frac{K}{1 + Ae^{-kt}}$

---

## Second-Order Linear Differential Equations

### Homogeneous with Constant Coefficients

Form: $ay'' + by' + cy = 0$

**Solution method:**
1. Characteristic equation: $ar^2 + br + c = 0$
2. Solve for $r$

**Three cases:**

#### Case 1: Two distinct real roots $r_1, r_2$
$$
y = C_1 e^{r_1 x} + C_2 e^{r_2 x}
$$

#### Case 2: Repeated real root $r$
$$
y = (C_1 + C_2 x)e^{rx}
$$

#### Case 3: Complex roots $r = \alpha \pm \beta i$
$$
y = e^{\alpha x}(C_1 \cos(\beta x) + C_2 \sin(\beta x))
$$

---

### Example Problems

**Example 1:** $y'' - 5y' + 6y = 0$

Characteristic equation: $r^2 - 5r + 6 = 0 \implies (r-2)(r-3) = 0$

Roots: $r_1 = 2$, $r_2 = 3$

**Solution:** $y = C_1 e^{2x} + C_2 e^{3x}$

---

**Example 2:** $y'' + 4y' + 4y = 0$

Characteristic equation: $r^2 + 4r + 4 = 0 \implies (r+2)^2 = 0$

Repeated root: $r = -2$

**Solution:** $y = (C_1 + C_2 x)e^{-2x}$

---

**Example 3:** $y'' + 4y = 0$

Characteristic equation: $r^2 + 4 = 0 \implies r = \pm 2i$

Complex roots: $\alpha = 0$, $\beta = 2$

**Solution:** $y = C_1 \cos(2x) + C_2 \sin(2x)$

---

## Nonhomogeneous Equations

Form: $ay'' + by' + cy = f(x)$

**General solution:** $y = y_h + y_p$

where:
- $y_h$: General solution of homogeneous equation
- $y_p$: Particular solution of nonhomogeneous equation

---

### Method of Undetermined Coefficients

**Strategy:** Guess form of $y_p$ based on $f(x)$

| $f(x)$ | Trial $y_p$ |
|--------|-------------|
| $ke^{ax}$ | $Ae^{ax}$ |
| $k\cos(bx)$ or $k\sin(bx)$ | $A\cos(bx) + B\sin(bx)$ |
| $kx^n$ | $A_nx^n + A_{n-1}x^{n-1} + \cdots + A_0$ |

**Modification rule:** If trial $y_p$ solves the homogeneous equation, multiply by $x$ (or $x^2$ if needed).

---

### Variation of Parameters

For $y'' + P(x)y' + Q(x)y = f(x)$ with known $y_h = C_1y_1 + C_2y_2$:

**Particular solution:**
$$
y_p = u_1y_1 + u_2y_2
$$

where:
$$
u_1 = -\int \frac{y_2 f}{W}\,dx, \quad u_2 = \int \frac{y_1 f}{W}\,dx
$$

and $W = y_1y_2' - y_1'y_2$ is the Wronskian.

---

## Applications of Second-Order DEs

### Simple Harmonic Motion

$$
m\frac{d^2x}{dt^2} + kx = 0
$$

**Solution:** $x(t) = A\cos(\omega t) + B\sin(\omega t)$ where $\omega = \sqrt{\frac{k}{m}}$

### Damped Harmonic Motion

$$
m\frac{d^2x}{dt^2} + c\frac{dx}{dt} + kx = 0
$$

Three cases based on discriminant:
- **Overdamped:** $c^2 > 4mk$
- **Critically damped:** $c^2 = 4mk$
- **Underdamped:** $c^2 < 4mk$

### Forced Oscillations

$$
m\frac{d^2x}{dt^2} + c\frac{dx}{dt} + kx = F_0\cos(\omega t)
$$

**Resonance** occurs when forcing frequency matches natural frequency.

---

## Series Solutions

For equations with variable coefficients, use power series:
$$
y = \sum_{n=0}^{\infty} a_n x^n
$$

**Method:**
1. Substitute series into DE
2. Collect coefficients of like powers
3. Find recurrence relation for $a_n$
4. Solve recurrence relation

---

## Laplace Transform Method

**Laplace Transform:**
$$
\mathcal{L}\{f(t)\} = F(s) = \int_0^{\infty} e^{-st}f(t)\,dt
$$

### Common Transforms

$$
\mathcal{L}\{1\} = \frac{1}{s}
$$

$$
\mathcal{L}\{e^{at}\} = \frac{1}{s-a}
$$

$$
\mathcal{L}\{\sin(at)\} = \frac{a}{s^2 + a^2}
$$

$$
\mathcal{L}\{\cos(at)\} = \frac{s}{s^2 + a^2}
$$

### Properties

$$
\mathcal{L}\{f'(t)\} = s\mathcal{L}\{f(t)\} - f(0)
$$

$$
\mathcal{L}\{f''(t)\} = s^2\mathcal{L}\{f(t)\} - sf(0) - f'(0)
$$

**Solution method:**
1. Take Laplace transform of both sides
2. Solve for $\mathcal{L}\{y\}$
3. Take inverse Laplace transform

---

## Systems of Differential Equations

### Linear System

$$
\frac{d\mathbf{x}}{dt} = A\mathbf{x}
$$

where $\mathbf{x}$ is a vector and $A$ is a matrix.

**Solution involves eigenvalues and eigenvectors of $A$.**

---

## Numerical Methods

### Euler's Method

$$
y_{n+1} = y_n + hf(x_n, y_n)
$$

where $h$ is step size.

### Runge-Kutta Methods

More accurate than Euler's method. Fourth-order Runge-Kutta (RK4) is common:

$$
y_{n+1} = y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)
$$

where:
$$
k_1 = f(x_n, y_n)
$$
$$
k_2 = f(x_n + h/2, y_n + hk_1/2)
$$
$$
k_3 = f(x_n + h/2, y_n + hk_2/2)
$$
$$
k_4 = f(x_n + h, y_n + hk_3)
$$

---

## Summary

- **First-order:** Separable, linear, exact, homogeneous, Bernoulli
- **Second-order homogeneous:** Solve characteristic equation
- **Second-order nonhomogeneous:** Find $y_h + y_p$
- **Applications:** Growth/decay, oscillations, cooling
- **Advanced methods:** Series solutions, Laplace transforms, numerical methods
- **Systems:** Matrix methods with eigenvalues
