# ML Cost

## Difficulty
- **Do we have a premade solution?**
- Depending on the problem, how difficult is it to implement, deliver, and maintain.

## Cost of Data
- Automatic data generation.
- Manual cost of data annotation.
- Amount of data needed.

## Need for Accuracy
- How costly is a wrong prediction?
- Lowest accuracy level below which the model becomes impractical.

---

# Estimating Complexity

## No Standard Complexity Estimation Model

### Major Unknowns
- Can the required quality be attained in practice?
- How much data is needed to reach the desired quality?
- How many features are required for the model to learn and generalize?
- How large should the model be?
- How long/much computation will it take?
- How many model trainings are required to reach the desired level?

---

## Rule of Thumb
- Required level of model accuracy ≥ 99% → Insufficient quantity of labeled data.
- In some problems, even 95% accuracy is considered very hard.
- Baseline = human performance → Typically a hard problem.

---

## Divide and Conquer


simplifying the problem
- make and educated guess
	- simplify
	- solve a simpler problem first