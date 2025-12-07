# F4: Overfitting Visualised — Educational Explanation Prompt

## Topic
Overfitting — When Your Model Memorizes Instead of Learns

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see training vs validation loss diverging and watch decision boundaries become overly complex.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Overfitting — When Your Model Memorizes Instead of Learns

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see training vs validation loss diverging and watch decision boundaries become overly complex.

**Prerequisites the learner should already understand**:
- Training and loss concepts (C5)
- What a decision boundary is (hyperplane separating classes)
- Basic idea of generalization

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand overfitting as memorizing training data
2. Know the train/validation loss divergence signature
3. See overfitting as overly complex decision boundaries
4. Know strategies to prevent overfitting
5. Understand the bias-variance tradeoff conceptually

**Required Sections**:
1. **What is Overfitting?**:
   - Model performs great on training data
   - Model performs poorly on new data
   - Has memorized rather than generalized
2. **The Train/Validation Gap**:
   - Training loss keeps decreasing
   - Validation loss starts increasing
   - Gap = overfitting
3. **Visual Signs**:
   - Decision boundary hugs every training point
   - Wiggly, complex boundaries
   - Fits noise, not signal
4. **Causes of Overfitting**:
   - Model too complex for data
   - Training too long
   - Too little training data
   - No regularization
5. **Prevention Strategies**:
   - Early stopping (stop before validation loss rises)
   - Regularization (L1, L2)
   - Dropout (randomly disable neurons)
   - Data augmentation (more training data)
   - Simpler model architecture
6. **Bias-Variance Tradeoff**:
   - Underfitting (high bias): too simple
   - Overfitting (high variance): too complex
   - Sweet spot: balanced
7. **Why This Matters for ML/AI**:
   - Overfitting is the central challenge
   - All practitioners must monitor and prevent it
   - Defines the whole field's approach to model evaluation

**Tone**: Use clear visual language. The "memorizing vs learning" metaphor is key.

**Length**: Approximately 1600-2000 words with practical prevention tips.
```
