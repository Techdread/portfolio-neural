# B3: The Gradient Vector — Educational Explanation Prompt

## Topic
The Gradient Vector — The Direction of Steepest Ascent

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see a 2D surface in 3D with an arrow pointing "uphill" and understand why the negative gradient is the direction of steepest descent.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Gradient Vector — The Direction of Steepest Ascent

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see a 2D surface in 3D with an arrow pointing "uphill" and understand why the negative gradient is the direction of steepest descent.

**Prerequisites the learner should already understand**:
- Partial derivatives (B2)
- Vectors as arrows with direction and magnitude (A1)
- 3D surfaces from f(x, y)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the gradient as a vector of all partial derivatives
2. Know that the gradient points in the direction of steepest increase
3. Understand why negative gradient = steepest decrease
4. Know the gradient magnitude indicates steepness
5. Connect directly to gradient descent optimization

**Required Sections**:
1. **From Individual Partials to a Vector** — Collecting ∂f/∂x, ∂f/∂y into ∇f
2. **Gradient Notation**: ∇f = (∂f/∂x, ∂f/∂y) or grad(f)
3. **The Key Property** — Gradient points in direction of steepest increase
   - Intuitive explanation: gradient combines "uphill" information from all directions
4. **Gradient Magnitude** — How steep is the steepest direction?
   - Flat areas have small gradient
   - Steep areas have large gradient
5. **Negative Gradient** — Flip the arrow to go downhill
6. **Gradient in the xy-Plane** — The gradient is a 2D vector lying in the input space, not pointing up the surface
7. **Why This Matters for ML/AI**:
   - Loss function is a surface over weight space
   - We want to go downhill (minimize loss)
   - Gradient tells us the direction of steepest descent
   - Gradient descent: weights = weights - learning_rate × gradient
8. **Gradient for N Variables** — Extends to millions of weights
9. **Computing Gradients** — Backpropagation is just efficient gradient computation

**Tone**: Make the "direction of steepest ascent" intuition crystal clear. Use the hiking/terrain analogy.

**Length**: Approximately 1600-2000 words, with strong emphasis on the ML connection.
```
