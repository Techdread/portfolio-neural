# F2: Backprop Gradient Flow — Educational Explanation Prompt

## Topic
Gradient Flow in Backpropagation — Vanishing and Exploding Gradients

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see gradients flowing backwards through a network, color-coded by magnitude, revealing vanishing and exploding gradient problems.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Gradient Flow in Backpropagation — Vanishing and Exploding Gradients

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see gradients flowing backwards through a network, color-coded by magnitude, revealing vanishing and exploding gradient problems.

**Prerequisites the learner should already understand**:
- Backpropagation basics (C2)
- Chain rule (B4)
- Activation functions (C4)

**Learning Objectives** — After reading this explanation, the learner should:
1. Visualize gradients flowing through layers
2. Understand gradient magnitude changes layer by layer
3. Know what vanishing gradients look like
4. Know what exploding gradients look like
5. Understand solutions (ReLU, residual connections, normalization)

**Required Sections**:
1. **Gradient Flow Recap** — Gradients multiply through layers (chain rule)
2. **Layer-by-Layer Multiplication**:
   - Each layer contributes a factor
   - Final gradient = product of all factors
3. **Vanishing Gradients**:
   - When factors < 1 repeatedly
   - Gradient shrinks exponentially
   - Early layers get near-zero gradients
   - Weights stop learning
   - Common with sigmoid/tanh
4. **Exploding Gradients**:
   - When factors > 1 repeatedly
   - Gradient grows exponentially
   - Weights update too much
   - Training becomes unstable (NaN)
   - Common in RNNs
5. **Diagnosing the Problem**:
   - Gradient histograms
   - Loss curves (stuck or exploding)
   - Weight update magnitudes
6. **Solutions**:
   - ReLU activation (gradient is 0 or 1)
   - Proper initialization (Xavier, He)
   - Batch normalization
   - Residual connections (skip connections)
   - Gradient clipping (for exploding)
7. **Why This Matters for ML/AI**:
   - Vanishing gradients = can't train deep networks
   - Solutions enabled modern deep learning
   - Understanding helps debug training issues

**Tone**: Focus on the visual intuition of gradients "dying" or "exploding" through layers.

**Length**: Approximately 1800-2200 words with clear problem-solution structure.
```
