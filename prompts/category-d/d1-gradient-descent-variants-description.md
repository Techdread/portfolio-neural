# D1: Gradient Descent Variants — Educational Explanation Prompt

## Topic
Gradient Descent Optimizers — From Vanilla to Adam

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see vanilla gradient descent, momentum, RMSprop, and Adam compared on the same loss surface, watching momentum escape local minima.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Gradient Descent Optimizers — From Vanilla to Adam

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see vanilla gradient descent, momentum, RMSprop, and Adam compared on the same loss surface, watching momentum escape local minima.

**Prerequisites the learner should already understand**:
- Gradient descent basics (B3)
- Loss functions (C5)
- What learning rate means

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand vanilla gradient descent and its limitations
2. Know how momentum accumulates velocity
3. Understand RMSprop's adaptive learning rates
4. See Adam as combining momentum and RMSprop
5. Know when to use each optimizer

**Required Sections**:
1. **Vanilla Gradient Descent**:
   - Update rule: θ = θ - α∇L
   - Problems: slow in ravines, stuck in local minima, sensitive to learning rate
2. **Momentum**:
   - Intuition: ball rolling downhill gains speed
   - Update rule with velocity term
   - v = βv + ∇L; θ = θ - αv
   - Dampens oscillations, accelerates in consistent directions
   - Can escape shallow local minima
3. **RMSprop (Root Mean Square Propagation)**:
   - Problem: different parameters need different learning rates
   - Adapt learning rate per parameter
   - Track squared gradient moving average
   - Divide gradient by sqrt of this average
   - Works well for non-stationary problems
4. **Adam (Adaptive Moment Estimation)**:
   - Best of both: momentum + adaptive rates
   - First moment (mean of gradients) = momentum
   - Second moment (variance of gradients) = RMSprop
   - Bias correction for early steps
   - Default choice for most deep learning
5. **Comparison Table**: Memory, computation, hyperparameters, typical use
6. **Why This Matters for ML/AI**:
   - Optimizer choice significantly affects training
   - Adam usually "just works"
   - Understanding helps diagnose training problems

**Tone**: Focus on intuition and practical guidance. Formulas are secondary to understanding.

**Length**: Approximately 2000-2500 words with clear comparisons and use-case guidance.
```
