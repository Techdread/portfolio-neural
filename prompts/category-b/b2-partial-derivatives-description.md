# B2: Partial Derivatives — Educational Explanation Prompt

## Topic
Partial Derivatives — Derivatives of Multivariable Functions

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see a 3D surface with slices showing change along each axis independently.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Partial Derivatives — Derivatives of Multivariable Functions

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see a 3D surface with slices showing change along each axis independently.

**Prerequisites the learner should already understand**:
- Derivatives of single-variable functions (B1)
- 3D coordinate systems (x, y, z)
- Functions with multiple inputs

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand functions of multiple variables as surfaces
2. Know that partial derivatives measure change in one direction only
3. Visualize partial derivatives as slopes of slice curves
4. Read partial derivative notation (∂f/∂x)
5. Connect partial derivatives to how neural network weights are updated individually

**Required Sections**:
1. **From One Variable to Many** — f(x) → f(x, y) → f(x, y, z, ...)
2. **Visualizing f(x, y)** — Height above the xy-plane as a surface
3. **The Problem** — A surface has infinitely many directions to go
4. **The Solution: One Direction at a Time** — Hold all other variables constant
5. **Partial Derivative Definition**:
   - ∂f/∂x: "How does f change as x changes (y held fixed)?"
   - ∂f/∂y: "How does f change as y changes (x held fixed)?"
6. **The Slice Interpretation**:
   - Fix y = c, get a curve in the xz-plane
   - ∂f/∂x is the slope of that curve
7. **Notation**:
   - ∂ (curly d) vs d (straight d)
   - Subscript notation: fₓ, f_y
8. **Computing Partial Derivatives** — Same rules as regular derivatives, treat other variables as constants
9. **Why This Matters for ML/AI**:
   - Neural networks have millions of parameters
   - We need to know how loss changes with respect to EACH weight
   - Partial derivatives tell us: "If I tweak this one weight, how does loss change?"
   - Backpropagation computes ALL partial derivatives efficiently
10. **The Gradient Preview** — Collecting all partials into a vector (leads to B3)

**Tone**: Emphasize the "one direction at a time" intuition. Use the slice visualization heavily.

**Length**: Approximately 1600-2000 words with clear examples and connection to ML.
```
