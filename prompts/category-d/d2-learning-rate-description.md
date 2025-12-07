# D2: Learning Rate Effects — Educational Explanation Prompt

## Topic
Learning Rate — The Most Important Hyperparameter

## Context
This is part of an interactive Three.js visualization portfolio. The learner will use an interactive slider to see: too small (slow), just right (convergent), too large (divergent) learning rates with real-time descent paths.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Learning Rate — The Most Important Hyperparameter

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will use an interactive slider to see: too small (slow), just right (convergent), too large (divergent) learning rates with real-time descent paths.

**Prerequisites the learner should already understand**:
- Gradient descent (B3, D1)
- What loss functions measure

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand learning rate as step size
2. See the symptoms of learning rate too small
3. See the symptoms of learning rate too large
4. Know strategies for finding good learning rates
5. Understand learning rate schedules

**Required Sections**:
1. **What is Learning Rate?** — Step size in parameter update
2. **Too Small**:
   - Symptoms: very slow convergence, gets stuck
   - Loss decreases but painfully slowly
   - Might not reach minimum in reasonable time
3. **Just Right**:
   - Steady, consistent descent
   - Loss decreases smoothly
   - Reaches good minimum efficiently
4. **Too Large**:
   - Symptoms: overshooting, oscillation, divergence
   - Loss increases or bounces around
   - May never converge
   - Can explode to infinity
5. **Finding Good Learning Rates**:
   - Learning rate finder (1cycle policy)
   - Start small, increase until loss explodes
   - Typical ranges for different optimizers
6. **Learning Rate Schedules**:
   - Step decay: reduce at fixed epochs
   - Exponential decay: continuous reduction
   - Cosine annealing: smooth decrease and increase
   - Warmup: start small, increase, then decay
7. **Why This Matters for ML/AI**:
   - Wrong learning rate = training failure
   - Often the first thing to tune
   - Adaptive optimizers help but don't solve everything

**Tone**: Practical and diagnostic. Help learners recognize symptoms in their own training.

**Length**: Approximately 1600-2000 words with clear visual descriptions of each scenario.
```
