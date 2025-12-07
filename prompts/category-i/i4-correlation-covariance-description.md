# I4: Correlation and Covariance — Educational Explanation Prompt

## Topic
Correlation and Covariance — Measuring Relationships Between Variables

## Context
This is part of an interactive Three.js visualization portfolio. The learner will drag points to change correlation, watch the covariance matrix update, and see eigenvectors of the covariance.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Correlation and Covariance — Measuring Relationships Between Variables

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will drag points to change correlation, watch the covariance matrix update, and see eigenvectors of the covariance.

**Prerequisites the learner should already understand**:
- Mean and variance (I1)
- What a scatter plot shows
- Matrices (A2)
- Eigenvectors (A5, basic idea)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand covariance as "how variables move together"
2. Know correlation as normalized covariance (-1 to 1)
3. Read and interpret covariance matrices
4. See eigenvectors as principal directions
5. Connect to PCA

**Required Sections**:
1. **Beyond Individual Variables** — How do two variables relate?
2. **Covariance**:
   - Measures joint variability
   - Positive: increase together
   - Negative: one up, one down
   - Zero: no linear relationship
   - Formula: Cov(X,Y) = E[(X-μₓ)(Y-μᵧ)]
3. **Correlation**:
   - Normalized covariance
   - Range: -1 to +1
   - +1: perfect positive linear relationship
   - -1: perfect negative linear relationship
   - 0: no linear relationship
   - Formula: Corr(X,Y) = Cov(X,Y) / (σₓσᵧ)
4. **The Covariance Matrix**:
   - Matrix of all pairwise covariances
   - Diagonal: variances
   - Off-diagonal: covariances
   - Always symmetric
5. **Visualizing Covariance**:
   - Scatter plot shape tells the story
   - Ellipse orientation = covariance sign
   - Ellipse elongation = correlation strength
6. **Eigenvectors of Covariance**:
   - Point in principal directions
   - Eigenvalues = variance in those directions
   - Largest eigenvalue = most variance
   - This IS PCA
7. **Why This Matters for ML/AI**:
   - Feature correlation affects models
   - Covariance matrix used in PCA
   - Gaussian distributions parameterized by covariance
   - Multivariate statistics throughout

**Tone**: Make the "moving together" intuition crystal clear. Correlation should feel natural.

**Length**: Approximately 1700-2100 words with clear examples and matrix explanation.
```
