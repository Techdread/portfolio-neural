# D3: Batch vs Stochastic vs Mini-batch — Educational Explanation Prompt

## Topic
Batch, Stochastic, and Mini-batch Gradient Descent

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see how gradient estimate noise/accuracy differs between variants and how this affects the descent path.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Batch, Stochastic, and Mini-batch Gradient Descent

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see how gradient estimate noise/accuracy differs between variants and how this affects the descent path.

**Prerequisites the learner should already understand**:
- Gradient descent basics (D1, D2)
- Loss as average over data points

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand batch GD uses all data per step
2. Understand stochastic GD uses one sample per step
3. Understand mini-batch GD as the practical middle ground
4. Know the trade-offs: accuracy vs speed vs noise
5. See how noise can help escape local minima

**Required Sections**:
1. **The Dataset Setting** — Loss is average over many data points
2. **Batch (Full) Gradient Descent**:
   - Compute gradient using ALL data
   - Accurate gradient estimate
   - Slow: must process entire dataset per step
   - Memory intensive
   - Smooth descent path
3. **Stochastic Gradient Descent (SGD)**:
   - Compute gradient using ONE sample
   - Noisy gradient estimate
   - Fast: one sample per step
   - Memory efficient
   - Zigzag descent path
   - Noise can escape local minima!
4. **Mini-batch Gradient Descent**:
   - Compute gradient using SUBSET of data (e.g., 32, 64, 128 samples)
   - Balanced noise vs accuracy
   - Efficient: vectorized operations on batch
   - The standard in practice
5. **Batch Size Effects**:
   - Larger batch = more accurate gradient, less noise
   - Smaller batch = more noise, faster updates
   - Very large batches can generalize poorly
6. **Why This Matters for ML/AI**:
   - Mini-batch is universal in deep learning
   - Batch size is a key hyperparameter
   - Some noise is actually beneficial

**Tone**: Clarify the confusing terminology (SGD often means mini-batch in practice). Practical focus.

**Length**: Approximately 1500-1800 words with clear comparisons.
```
