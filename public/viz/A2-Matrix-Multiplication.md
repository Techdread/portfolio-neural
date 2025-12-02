# Matrix Multiplication: The Engine of Neural Networks

You've mastered vectors—arrows in space, lists of numbers that can be added and scaled. Now it's time to meet their powerful sibling: the **matrix**. If vectors are the nouns of linear algebra, matrices are the verbs. They *do* things to vectors. Every neural network layer, every 3D graphics transformation, every recommendation system—matrices are doing the heavy lifting.


## 1. What is a Matrix?

A matrix is just a rectangular grid of numbers. That's it. But like many simple things in mathematics, this humble grid turns out to be extraordinarily useful because we can interpret it in multiple ways.

**Think of a matrix as:**

**A table of numbers** — The most literal interpretation. Just like a spreadsheet with rows and columns:

```typescript
const matrix = [
  [1, 2, 3],
  [4, 5, 6]
];
```

**A collection of vectors** — You can read a matrix as a stack of row vectors (reading horizontally) or as a set of column vectors standing side by side (reading vertically). This dual interpretation becomes crucial when we multiply.

**A transformation function** — Here's where it gets interesting. A matrix can represent a *function* that takes a vector as input and produces a new vector as output. Feed in a point, get back a transformed point. This is how 3D graphics engines rotate and scale objects, and how neural networks transform data layer by layer.

**A lookup/mapping table** — In ML contexts, think of weight matrices as encoding which input features influence which outputs, and by how much.


## 2. Matrix Dimensions

We describe matrix size as **rows × columns** (always rows first). A matrix with 2 rows and 3 columns is a "2×3 matrix" or "2 by 3 matrix."

```typescript
// A 2×3 matrix: 2 rows, 3 columns
const A: number[][] = [
  [1, 2, 3],    // row 0
  [4, 5, 6]     // row 1
];
// Columns: 0  1  2

// Shape in NumPy/TensorFlow style: (2, 3)
```

**The compatibility rule for multiplication:** To multiply matrix A by matrix B (written AB), the number of **columns in A** must equal the number of **rows in B**.

```
A: (m × n)  ×  B: (n × p)  =  C: (m × p)
         ↑___↑
    These must match!
```

Think of it like connecting LEGO blocks—the "output width" of the first matrix must match the "input height" of the second. If A is 2×3 and B is 3×4, the result is 2×4. If A is 2×3 and B is 2×4? Error. They don't connect.


## 3. The Row-by-Column Algorithm

Matrix multiplication isn't just multiplying corresponding elements (that's a different operation called element-wise or Hadamard product). Instead, each element in the result comes from a **dot product** between a row of the first matrix and a column of the second.

Let's work through a concrete example: multiplying a 2×3 matrix by a 3×2 matrix.

```typescript
// A is 2×3
const A = [
  [1, 2, 3],
  [4, 5, 6]
];

// B is 3×2
const B = [
  [7, 8],
  [9, 10],
  [11, 12]
];

// Result C will be 2×2
```

**The algorithm:** For position (i, j) in the result, take row i from A, take column j from B, compute their dot product.

```
C[0][0] = (row 0 of A) · (column 0 of B)
        = [1, 2, 3] · [7, 9, 11]
        = 1×7 + 2×9 + 3×11
        = 7 + 18 + 33 = 58

C[0][1] = (row 0 of A) · (column 1 of B)
        = [1, 2, 3] · [8, 10, 12]
        = 1×8 + 2×10 + 3×12
        = 8 + 20 + 36 = 64

C[1][0] = (row 1 of A) · (column 0 of B)
        = [4, 5, 6] · [7, 9, 11]
        = 4×7 + 5×9 + 6×11
        = 28 + 45 + 66 = 139

C[1][1] = (row 1 of A) · (column 1 of B)
        = [4, 5, 6] · [8, 10, 12]
        = 4×8 + 5×10 + 6×12
        = 32 + 50 + 72 = 154
```

**Result:**
```typescript
const C = [
  [58, 64],
  [139, 154]
];
```

Here's what that looks like as code:

```typescript
function matmul(A: number[][], B: number[][]): number[][] {
  const m = A.length;        // rows in A
  const n = A[0].length;     // cols in A (must equal rows in B)
  const p = B[0].length;     // cols in B
  
  const C: number[][] = [];
  
  for (let i = 0; i < m; i++) {
    C[i] = [];
    for (let j = 0; j < p; j++) {
      let sum = 0;
      for (let k = 0; k < n; k++) {
        sum += A[i][k] * B[k][j];  // row i of A, column j of B
      }
      C[i][j] = sum;
    }
  }
  return C;
}
```

Notice the three nested loops—this is why matrix multiplication is O(n³) for square matrices. It's computationally expensive, which is why GPUs (massively parallel processors) revolutionised deep learning.


## 4. Why Order Matters: AB ≠ BA

Unlike regular number multiplication (3 × 5 = 5 × 3), matrix multiplication is **not commutative**. Swapping the order gives a different result—or might not even be valid.

**Dimension incompatibility:** If A is 2×3 and B is 3×4, then AB exists (result is 2×4), but BA doesn't exist at all (4 columns doesn't match 2 rows).

**Different results even when both are valid:** Even when both orders work (like with square matrices), you typically get different answers.

**Geometric intuition:** Imagine two transformations—a 90° rotation and a 2× horizontal stretch.

Rotate then stretch: Take a square, rotate it 45° so it's a diamond, then stretch horizontally. You get a wide diamond.

Stretch then rotate: Take a square, stretch it into a wide rectangle, then rotate. You get a tall rectangle at an angle.

Completely different results! The order of transformations matters, and matrix multiplication order reflects this. When you write AB and apply it to a vector v, you're computing A(Bv)—B acts first, then A acts on the result. Reading right to left might feel backwards, but it matches function composition: (f ∘ g)(x) = f(g(x)).


## 5. Matrices as Transformations

This is where matrices become visual and intuitive. A 2×2 matrix transforms 2D space; a 3×3 matrix transforms 3D space. Let's see the classic examples:

**Identity Matrix — "Do nothing"**
```typescript
const I = [
  [1, 0],
  [0, 1]
];
// Multiplying any vector by I returns the same vector
// I × [x, y] = [x, y]
```

**Scaling Matrix — "Stretch or shrink"**
```typescript
const scale = [
  [2, 0],   // Scale x by 2
  [0, 3]    // Scale y by 3
];
// [x, y] → [2x, 3y]
```

**Rotation Matrix — "Rotate space"**
```typescript
// Rotate by angle θ counterclockwise
const rotate = (theta: number) => [
  [Math.cos(theta), -Math.sin(theta)],
  [Math.sin(theta),  Math.cos(theta)]
];
// This is worth memorising—it appears everywhere in graphics and physics
```

**Shear Matrix — "Skew space"**
```typescript
const shearX = [
  [1, 0.5],  // x gets shifted by 0.5*y
  [0, 1]
];
// Turns rectangles into parallelograms
```

Your Three.js visualization will show these beautifully—watch how the entire coordinate grid warps when you apply each transformation. Every point moves simultaneously according to the same rule encoded in the matrix.


## 6. Why This Matters for ML/AI

Here's where everything clicks together for neural networks.

**Neural network layers ARE matrix multiplications.** A dense (fully connected) layer takes an input vector, multiplies it by a weight matrix, adds a bias, and applies an activation function:

```typescript
// Single layer forward pass (simplified)
function denseLayer(input: Vector, weights: Matrix, bias: Vector): Vector {
  return activate(matmul(weights, input) + bias);
}
```

**Weight matrices encode learned relationships.** Each entry W[i][j] represents "how much does input feature j influence output neuron i?" Training a neural network means adjusting these matrix entries.

**Batch processing is matrix multiplication.** Instead of processing one input at a time, stack N inputs as columns in a matrix. One matrix multiplication processes the entire batch:

```typescript
// inputs: (features × batch_size)
// weights: (neurons × features)  
// outputs: (neurons × batch_size)  ← all N outputs computed at once!
const outputs = matmul(weights, inputs);
```

This is why GPUs matter—they're designed for exactly this kind of parallel matrix operation.

**Understanding shapes prevents bugs.** The most common error in deep learning code is dimension mismatch. If your layer expects (784,) inputs (flattened 28×28 images) but receives (28, 28), you'll get a shape error. Understanding how dimensions flow through matrix multiplications helps you debug instantly:

```
Input: (batch_size, 784)
Layer 1 weights: (784, 256)  →  Output: (batch_size, 256)
Layer 2 weights: (256, 128)  →  Output: (batch_size, 128)
Layer 3 weights: (128, 10)   →  Output: (batch_size, 10)
```


## 7. The Programming Perspective

In practice, you'll never write nested loops for matrix multiplication—libraries handle it efficiently.

**NumPy:**
```python
import numpy as np
C = np.matmul(A, B)   # Explicit
C = A @ B              # Python 3.5+ operator (preferred)
```

**TensorFlow/PyTorch:**
```python
C = tf.matmul(A, B)   # TensorFlow
C = torch.mm(A, B)     # PyTorch (2D only)
C = torch.matmul(A, B) # PyTorch (handles batches)
```

**JavaScript (for your Three.js work):**
```typescript
// Three.js Matrix4 class handles 4×4 transformations
const m = new THREE.Matrix4();
m.multiply(otherMatrix);  // In-place multiplication
```

**Broadcasting hint:** Modern frameworks can handle "batch" dimensions automatically. A weight matrix (256, 128) multiplied with a batch (32, 256) broadcasts correctly to produce (32, 128). The rules can be subtle—consult documentation when shapes get complex.


## 8. Common Pitfalls

**Shape mismatch errors:** The inner dimensions must match. If you're getting "shapes (X, Y) and (Z, W) not aligned," check that Y equals Z. Sketch out your expected shapes on paper.

**Confusing @ with \*:** In NumPy, `A * B` is element-wise multiplication (same shape required), while `A @ B` is matrix multiplication. This catches everyone at least once.

**Forgetting that order matters:** `weights @ inputs` is not the same as `inputs @ weights`. Convention varies—some frameworks expect (batch, features), others (features, batch). Read the docs.

**Transposition confusion:** Sometimes you need to transpose a matrix (flip rows and columns) to make dimensions align. If A is (m, n), then A.T is (n, m). Common pattern: `X @ W.T` or `W.T @ X` depending on your convention.

**Off-by-one with batch dimensions:** Is your input shape (784,) or (1, 784) or (784, 1)? These are different: a 1D array versus a row vector versus a column vector. Frameworks sometimes reshape automatically, sometimes don't.


## Wrapping Up

Matrix multiplication is deceptively simple in definition—row times column, sum the products—but unlocks extraordinary power. You've learned that matrices can represent transformations of space, that order matters because transformations don't commute, and that neural networks are fundamentally stacks of matrix multiplications learning useful transformations of data.

In your Three.js visualization, watch how applying a matrix warps the entire grid. That warping is exactly what happens to data flowing through a neural network—each layer transforms the representation, bending and stretching the feature space until the final output separates cats from dogs, or predicts tomorrow's weather, or generates the next word in a sentence.

Next up: we'll see how these ideas extend to tensors—matrices with more dimensions—and how backpropagation uses matrix calculus to learn those transformations.
