# A4: Tensor Visualiser — Educational Explanation Prompt

## Topic
Tensors — From Scalars to N-Dimensional Arrays

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see tensors of increasing dimensionality and operations like reshaping, broadcasting, and slicing.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Tensors — From Scalars to N-Dimensional Arrays

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see tensors of increasing dimensionality and operations like reshaping, broadcasting, and slicing.

**Prerequisites the learner should already understand**:
- Vectors (A1) and Matrices (A2)
- Arrays in programming
- Basic neural network concepts (helpful but not required)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the tensor hierarchy: scalar → vector → matrix → 3D tensor → N-D tensor
2. Know what tensor "shape" and "rank" mean
3. Understand reshaping and why it's useful
4. Grasp broadcasting rules intuitively
5. Know how to slice and index tensors
6. Connect tensor operations to neural network data flow

**Required Sections**:
1. **What is a Tensor?** — Generalization of vectors and matrices to any number of dimensions
2. **The Tensor Hierarchy**:
   - Rank 0: Scalar (single number) — a loss value
   - Rank 1: Vector (1D array) — a bias vector
   - Rank 2: Matrix (2D array) — a weight matrix, grayscale image
   - Rank 3: 3D tensor — RGB image (height × width × channels), batch of vectors
   - Rank 4+: Batch of images, video, etc.
3. **Shape, Rank, and Size**:
   - Shape: tuple of dimension sizes
   - Rank: number of dimensions
   - Size: total number of elements
4. **Reshaping** — Same data, different shape
   - Flattening (image to vector for dense layer)
   - Expanding dimensions (for broadcasting)
   - Common reshapes in neural networks
5. **Broadcasting** — How operations work on mismatched shapes
   - Rules explained simply
   - Visual examples
   - Common broadcasting patterns in ML
6. **Slicing and Indexing** — Extracting sub-tensors
   - Single element access
   - Slice notation
   - Advanced indexing
7. **Why This Matters for ML/AI**:
   - All neural network data is tensors
   - Shape errors are the most common bugs
   - Understanding broadcasting prevents confusion
   - Reshaping connects different layer types

**Include**: TensorFlow.js and NumPy code snippets showing each operation.

**Length**: Approximately 2000-2500 words with clear diagrams described and code examples.
```
