# A2: Matrix Multiplication — Educational Explanation Prompt

## Topic
Matrix Multiplication

## Context
This is part of an interactive Three.js visualization portfolio teaching neural network mathematics. The learner will see an interactive visualization showing row-by-column multiplication step-by-step and matrices transforming space.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Matrix Multiplication

**Context**: This is part of an interactive Three.js visualization portfolio teaching neural network mathematics. The learner will see an interactive visualization showing row-by-column multiplication step-by-step and matrices transforming space.

**Prerequisites the learner should already understand**:
- Vectors and vector operations (covered in A1)
- Basic 2D coordinate systems
- Arrays and nested arrays in programming

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand what a matrix represents (a collection of vectors, a transformation, a lookup table)
2. Know the row-by-column rule for matrix multiplication
3. Understand why matrix multiplication order matters (AB ≠ BA)
4. Visualize matrices as transformations of space (rotation, scaling, shearing)
5. Connect matrix multiplication to neural network forward passes

**Required Sections**:
1. **What is a Matrix?** — Think of it as:
   - A table of numbers
   - A collection of row vectors or column vectors
   - A function that transforms inputs to outputs
2. **Matrix Dimensions** — Rows × Columns notation, compatibility rules
3. **The Row-by-Column Algorithm** — Step-by-step with small concrete example (2×3 times 3×2)
4. **Why Order Matters** — AB ≠ BA with geometric intuition (rotate then scale vs scale then rotate)
5. **Matrices as Transformations** — Visual examples:
   - Identity matrix (do nothing)
   - Scaling matrix (stretch/shrink)
   - Rotation matrix (rotate space)
   - Shear matrix (skew space)
6. **Why This Matters for ML/AI**:
   - Neural network layers are matrix multiplications
   - Weight matrices transform activations
   - Batch processing: multiply many inputs at once
   - Understanding shapes prevents dimension mismatch errors
7. **The Programming Perspective** — NumPy/TensorFlow notation, broadcasting hints
8. **Common Pitfalls** — Shape mismatches, confusing element-wise vs matrix multiply

**Tone**: Conversational but precise. Use code analogies (matrices as 2D arrays, multiplication as nested loops). Include TypeScript-style pseudocode where helpful.

**Length**: Comprehensive — approximately 1800-2200 words with clear section headings and worked examples.
```
