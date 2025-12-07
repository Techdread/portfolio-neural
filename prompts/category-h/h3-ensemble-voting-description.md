# H3: Ensemble Voting Visualiser — Educational Explanation Prompt

## Topic
Ensemble Methods — Combining Multiple Models

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see multiple models making predictions with votes combining visually to produce ensemble predictions.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Ensemble Methods — Combining Multiple Models

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see multiple models making predictions with votes combining visually to produce ensemble predictions.

**Prerequisites the learner should already understand**:
- Classification basics
- What different model types are (trees, neural nets, etc.)
- Probability and confidence

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand ensemble methods combine multiple models
2. Know different voting schemes (hard voting, soft voting, weighted)
3. Understand why ensembles often outperform single models
4. Know common ensemble methods (bagging, boosting, stacking)
5. See the bias-variance perspective on ensembles

**Required Sections**:
1. **The Wisdom of Crowds** — Multiple opinions often better than one
2. **Why Ensembles Work**:
   - Different models make different errors
   - Errors cancel out on average
   - Reduces variance while maintaining low bias
3. **Voting Schemes**:
   - Hard voting: majority class wins
   - Soft voting: average probabilities, then decide
   - Weighted voting: some models count more
4. **Types of Ensembles**:
   - Bagging (Random Forest): parallel, independent models
   - Boosting (XGBoost, AdaBoost): sequential, focus on errors
   - Stacking: models feed into meta-model
5. **Diversity is Key**:
   - Ensemble of identical models = single model
   - Need models that disagree (on different samples)
   - Different algorithms, different data subsets
6. **Bias-Variance View**:
   - Bagging reduces variance (averaging stabilizes)
   - Boosting reduces bias (focusing on errors)
7. **Practical Considerations**:
   - More compute at inference time
   - Harder to interpret
   - Usually worth it for important predictions
8. **Why This Matters for ML/AI**:
   - Ensembles win competitions (Kaggle)
   - Production systems often use ensembles
   - Random Forest is based on ensemble principles

**Tone**: Use the voting/democracy metaphor heavily. Make combination feel democratic and intuitive.

**Length**: Approximately 1500-1900 words with clear ensemble type explanations.
```
