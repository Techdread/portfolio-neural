# D4: Regularisation Visualised — Educational Explanation Prompt

## Topic
Regularisation — L1 and L2 Penalties

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see L1 (diamond) vs L2 (circle) constraint regions and understand why L1 promotes sparsity.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Regularisation — L1 and L2 Penalties

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see L1 (diamond) vs L2 (circle) constraint regions and understand why L1 promotes sparsity.

**Prerequisites the learner should already understand**:
- Loss functions (C5)
- Gradient descent (D1)
- What overfitting means

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand regularisation as a constraint on weights
2. Know L2 regularisation (Ridge, weight decay)
3. Know L1 regularisation (Lasso)
4. Visualize constraint regions geometrically
5. Understand why L1 gives sparse solutions

**Required Sections**:
1. **The Overfitting Problem** — Model fits training data too well, fails on new data
2. **Regularisation Idea** — Penalize large weights to keep model simple
3. **L2 Regularisation (Ridge)**:
   - Add ||w||² to loss
   - Penalty grows quadratically with weight magnitude
   - Constraint region is a circle/sphere
   - Pushes weights toward zero but rarely exactly zero
   - Also called "weight decay"
4. **L1 Regularisation (Lasso)**:
   - Add ||w||₁ to loss
   - Penalty grows linearly with weight magnitude
   - Constraint region is a diamond
   - Pushes weights to EXACTLY zero (sparsity!)
   - Feature selection effect
5. **The Geometric Intuition**:
   - Loss contours want to expand
   - Constraint region limits expansion
   - Optimal point where contour touches constraint
   - Diamond corners touch first → sparse solution
6. **Combined (Elastic Net)** — Mix of L1 and L2
7. **Why This Matters for ML/AI**:
   - Regularisation prevents overfitting
   - L2 is default (weight decay in optimizers)
   - L1 for feature selection or when sparsity desired
   - Trade-off via regularisation strength (λ)

**Tone**: Focus heavily on the geometric intuition. The "why L1 = sparsity" insight is the key takeaway.

**Length**: Approximately 1600-2000 words with geometric explanations.
```
