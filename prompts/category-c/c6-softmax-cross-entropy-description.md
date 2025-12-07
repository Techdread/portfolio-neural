# C6: Softmax & Cross-Entropy — Educational Explanation Prompt

## Topic
Softmax and Cross-Entropy — From Scores to Probabilities to Loss

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see logits transformed to probabilities and then to loss, with emphasis on the harsh penalty for confident wrong predictions.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Softmax and Cross-Entropy — From Scores to Probabilities to Loss

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see logits transformed to probabilities and then to loss, with emphasis on the harsh penalty for confident wrong predictions.

**Prerequisites the learner should already understand**:
- Basic probability (numbers 0-1 summing to 1)
- Exponential function (e^x)
- Logarithm basics
- Loss functions concept (C5)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand logits as raw, unnormalized scores
2. Know how softmax converts logits to probabilities
3. Understand cross-entropy loss for multi-class classification
4. See why confident wrong predictions are severely penalized
5. Understand numerical stability (log-sum-exp trick)

**Required Sections**:
1. **The Classification Pipeline**: logits → softmax → probabilities → cross-entropy → loss
2. **What are Logits?** — Raw output scores, can be any real number
3. **Softmax Function**:
   - Formula: softmax(zᵢ) = e^zᵢ / Σⱼe^zⱼ
   - Properties: outputs sum to 1, all positive
   - Intuition: exponential makes bigger scores much bigger
   - Temperature parameter (optional)
4. **Why Softmax?**:
   - Differentiable (unlike argmax)
   - Preserves relative ordering
   - Gives probability interpretation
5. **Cross-Entropy Loss for Multi-class**:
   - Formula: L = -Σᵢyᵢlog(pᵢ) = -log(p_correct)
   - Only the correct class matters (one-hot encoding)
   - Minimizing = maximizing probability of correct class
6. **The Harsh Penalty**:
   - If model is confident AND wrong: -log(small number) = huge loss
   - If model is confident AND right: -log(large number) = small loss
   - Numerical example with extreme cases
7. **Numerical Stability**:
   - e^big number = overflow
   - log(small number) = -infinity
   - The log-sum-exp trick
8. **Why This Matters for ML/AI**:
   - Classification networks end with softmax
   - Cross-entropy is the standard classification loss
   - Understanding prevents debugging nightmares

**Tone**: Walk through the pipeline step by step. Make the log penalties intuitive.

**Length**: Approximately 1800-2200 words with numerical examples throughout.
```
