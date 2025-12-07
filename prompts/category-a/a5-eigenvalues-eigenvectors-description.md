# A5: Eigenvalues & Eigenvectors — Educational Explanation Prompt

## Topic
Eigenvalues and Eigenvectors

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see eigenvectors as special vectors that only scale (don't rotate) under matrix transformation.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Eigenvalues and Eigenvectors

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see eigenvectors as special vectors that only scale (don't rotate) under matrix transformation.

**Prerequisites the learner should already understand**:
- Vectors and vector operations (A1)
- Matrix transformations (A2, A3)
- What scaling a vector means

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand eigenvectors as "direction-preserving" vectors under transformation
2. Know that eigenvalues tell us the scaling factor
3. Visualize what eigenvectors look like for various matrices
4. Understand the connection to PCA (dimensionality reduction)
5. Grasp why eigen-decomposition reveals matrix structure

**Required Sections**:
1. **The Key Intuition** — Most vectors get rotated and scaled by a matrix. Eigenvectors only get scaled.
2. **Definition Made Visual**:
   - Av = λv explained in plain language
   - "A transforms v to a scaled version of itself"
3. **Finding Eigenvectors** — High-level process (not full computation):
   - det(A - λI) = 0 to find eigenvalues
   - Solve (A - λI)v = 0 for eigenvectors
4. **Visual Examples**:
   - 2×2 scaling matrix (easy case: axis vectors are eigenvectors)
   - 2×2 rotation matrix (no real eigenvectors — everything rotates)
   - Shear matrix (one eigenvector along shear axis)
   - Symmetric matrix (orthogonal eigenvectors)
5. **Eigenvalue Meaning**:
   - λ > 1: stretching
   - 0 < λ < 1: compression
   - λ < 0: flip direction
   - λ = 0: collapse to lower dimension
6. **Why This Matters for ML/AI**:
   - **PCA**: Eigenvectors of covariance matrix are principal components
   - **Stability Analysis**: Gradient descent convergence
   - **Graph Neural Networks**: Spectral methods use Laplacian eigenvectors
   - **SVD**: Closely related (singular values)
7. **Connection to PCA** — Eigenvectors point in directions of maximum variance

**Tone**: Focus heavily on visual intuition. Math notation is secondary to understanding.

**Length**: Approximately 1600-2000 words with emphasis on examples and ML applications.
```
