# Basis Vectors and Change of Basis: The Coordinates Behind Coordinates

Here's a question that sounds simple but opens up deep insights: when you say a point is at (3, 2), what does that actually mean? The answer is: it depends on your coordinate system. And your coordinate system is defined by your **basis vectors**.

Understanding basis vectors reveals something profound: coordinates are just descriptions, not intrinsic properties. The same point in space can be (3, 2) in one system and (1, 5) in another. Neither is "right." They're just different ways of describing the same location. This concept is fundamental to understanding how neural networks learn representations and why techniques like PCA work.


## 1. What are Basis Vectors?

Basis vectors are the "measuring sticks" that define a coordinate system. They answer two questions:
- What direction does each axis point?
- How long is "one unit" along each axis?

When you write coordinates like (3, 2), you're implicitly saying: "Go 3 units along the first measuring stick, then 2 units along the second measuring stick."

```typescript
// Coordinates are instructions for combining basis vectors
const point = [3, 2];  // But 3 of WHAT? 2 of WHAT?

// The basis vectors answer that question
const basis1 = [1, 0];  // First measuring stick
const basis2 = [0, 1];  // Second measuring stick

// The actual position is:
// position = 3 * basis1 + 2 * basis2
//          = 3 * [1, 0] + 2 * [0, 1]
//          = [3, 0] + [0, 2]
//          = [3, 2]
```

Think of it like giving directions. "Walk 3 blocks east, then 2 blocks north" only makes sense if we agree on what "east" and "north" mean, and how long a "block" is.


## 2. The Standard Basis

The coordinate system you learned in school uses the **standard basis**:

```typescript
// 2D Standard Basis
const i = [1, 0];  // Points right, length 1
const j = [0, 1];  // Points up, length 1

// 3D Standard Basis
const i = [1, 0, 0];  // X-axis
const j = [0, 1, 0];  // Y-axis
const k = [0, 0, 1];  // Z-axis
```

These basis vectors are perpendicular (orthogonal) and have length 1 (normalized). This combination is called an **orthonormal** basis, and it's wonderfully convenient because the math stays clean.

But here's the thing: there's nothing sacred about these directions. We chose them by convention. The universe doesn't have a preferred "right" direction. Any set of vectors that spans the space and isn't redundant can serve as a basis.


## 3. Linear Combinations

Every vector in a space can be written as a **linear combination** of the basis vectors. "Linear combination" just means "add up scaled versions."

```typescript
function vectorFromCoordinates(
  coords: number[], 
  basis: number[][]
): number[] {
  // coords[i] tells us how much of basis[i] to use
  let result = new Array(basis[0].length).fill(0);
  
  for (let i = 0; i < coords.length; i++) {
    for (let j = 0; j < result.length; j++) {
      result[j] += coords[i] * basis[i][j];
    }
  }
  return result;
}

// Example: (3, 2) in standard basis
const standardBasis = [[1, 0], [0, 1]];
const coords = [3, 2];
const position = vectorFromCoordinates(coords, standardBasis);
// position = [3, 2]
```

This is the fundamental equation:

```
v = c₁·b₁ + c₂·b₂ + ... + cₙ·bₙ
```

Where `v` is the vector, `cᵢ` are the coordinates (scalars), and `bᵢ` are the basis vectors.


## 4. Non-Standard Bases

Now let's get interesting. What if we use different measuring sticks?

```typescript
// A different basis (still orthogonal, but rotated 45°)
const u = [0.707, 0.707];   // Points diagonally up-right
const v = [-0.707, 0.707];  // Points diagonally up-left

// Same coordinates (3, 2) but different meaning!
// 3 units along u, 2 units along v
const position = vectorFromCoordinates([3, 2], [u, v]);
// position ≈ [0.707, 3.535]  (different actual location!)
```

Or an even stranger basis:

```typescript
// Non-orthogonal basis (skewed)
const b1 = [1, 0];     // Still points right
const b2 = [0.5, 1];   // Points up and slightly right

// (3, 2) in this basis means something different again
const position = vectorFromCoordinates([3, 2], [b1, b2]);
// position = [4, 2]  (the 2 units of b2 added 1 to x)
```

Non-orthogonal bases are harder to work with mentally but perfectly valid mathematically. They appear naturally in crystallography, some neural network architectures, and anywhere structure isn't perfectly aligned with convenient axes.


## 5. Same Point, Different Coordinates

This is the key insight that makes everything click.

Imagine a red dot painted on the floor. That dot has a fixed position in physical space. It doesn't move. But its coordinates depend entirely on where you put your axes.

```typescript
// The SAME physical point
const physicalPosition = [3, 2];  // In standard coordinates

// Described in a rotated coordinate system (45° rotation)
const rotatedCoords = [3.54, -0.71];  // Same point!

// Described in a scaled coordinate system (units twice as big)
const scaledCoords = [1.5, 1.0];  // Same point!
```

Your Three.js visualization will show this beautifully: as the basis vectors rotate or stretch, the grid lines move with them, but a marked point stays fixed. Its numerical coordinates change to compensate.

Real-world analogy: The Eiffel Tower is at the same location whether you describe it in latitude/longitude, UTM coordinates, or "3 blocks from my hotel." The description changes; the tower doesn't move.


## 6. Change of Basis Matrix

To convert coordinates from one basis to another, we use a **change of basis matrix**. This matrix answers: "If I know the coordinates in basis A, what are the coordinates in basis B?"

```typescript
// Basis A: standard
const A = [[1, 0], [0, 1]];

// Basis B: rotated 45°
const B = [[0.707, 0.707], [-0.707, 0.707]];

// To go from A-coordinates to B-coordinates:
// We need the inverse of the matrix whose columns are B's vectors
// expressed in A's coordinates

// Change of basis matrix (B to A): columns are B's basis vectors
const B_to_A = [
  [0.707, -0.707],
  [0.707, 0.707]
];

// Change of basis matrix (A to B): inverse of above
const A_to_B = [
  [0.707, 0.707],
  [-0.707, 0.707]
];

// Convert point [3, 2] from A to B
function matVecMul(M, v) {
  return [
    M[0][0]*v[0] + M[0][1]*v[1],
    M[1][0]*v[0] + M[1][1]*v[1]
  ];
}

const coordsInA = [3, 2];
const coordsInB = matVecMul(A_to_B, coordsInA);
// coordsInB ≈ [3.54, -0.71]
```

The beautiful thing: this transformation is just matrix multiplication. Every coordinate conversion, every rotation, every scaling can be expressed as multiplying by the right matrix.


## 7. Why This Matters for ML/AI

Basis vectors aren't just abstract math. They're central to how neural networks represent and process information.

**Embeddings are coordinates in a learned basis.** When a word embedding model outputs a 300-dimensional vector for "cat", those 300 numbers are coordinates. But coordinates relative to what? The model has learned its own basis, where each dimension captures some aspect of meaning. We don't explicitly know what each axis represents, but the model found a basis where similar words cluster together.

```python
# Word embedding: coordinates in learned semantic space
cat_embedding = model.encode("cat")    # [0.23, -0.15, 0.87, ...]
dog_embedding = model.encode("dog")    # [0.21, -0.12, 0.82, ...]
# Similar coordinates because similar meaning (in the model's basis)
```

**Different layers use different coordinate systems.** As data flows through a neural network, each layer transforms it into a new representation. Conceptually, each layer is expressing the data in a new basis that's more useful for the task. Early layers might use a basis that separates edges from textures; later layers might use a basis that separates cats from dogs.

**PCA finds a better basis.** Remember eigenvalues and eigenvectors? PCA is literally finding a new basis (the principal components) where the first axis captures the most variance, the second captures the second-most, and so on. You're not changing the data; you're changing the coordinate system to one where the important structure aligns with the axes.

```python
# Original data: 100 dimensions, but most variance in 3 directions
pca = PCA(n_components=3)
transformed = pca.fit_transform(data)
# Same data points, new coordinates in better basis
```

**Attention mechanisms project into different spaces.** In transformers, the Query, Key, and Value projections are literally changes of basis. The same input is described in three different coordinate systems, each optimised for a different purpose:

```python
Q = input @ W_q  # Project to query space
K = input @ W_k  # Project to key space  
V = input @ W_v  # Project to value space
```

The learned weight matrices `W_q`, `W_k`, `W_v` are change-of-basis matrices. The model learns bases where the dot product between queries and keys meaningfully captures which tokens should attend to which.

**Transfer learning aligns embedding spaces.** When you fine-tune a pretrained model, you're often learning how to map between the model's internal basis and your task's requirements. When combining models trained separately, researchers sometimes need to explicitly learn a transformation matrix to align their embedding spaces.


## 8. Visual Intuition

The visualisation makes this tangible. You'll see:

**The grid defines the basis.** In standard coordinates, grid lines are horizontal and vertical. When you change basis, the grid skews and rotates with it. The grid lines always stay parallel to the basis vectors.

**Points stay fixed while coordinates change.** Mark a point. As you rotate or scale the basis, watch the grid move around the point. The point's position in the viewport doesn't change, but the numbers describing it do.

**Coordinates are instructions.** Following coordinates means "walk along the grid lines." (2, 3) means walk 2 grid squares in the first direction, then 3 in the second. Same instructions, different grids, different destinations.

**Orthogonal vs skewed.** With an orthogonal basis, the grid squares are rectangles. With a skewed basis, they become parallelograms. Both are valid, but orthogonal is easier to reason about.


## Wrapping Up

Coordinates are descriptions, not destinations. The same point in space can have infinitely many different coordinate descriptions, depending on which basis you choose. Changing basis doesn't change reality; it changes how you talk about reality.

This perspective is liberating. When you see a 512-dimensional embedding vector, you don't need to ask "what is dimension 237?" There probably isn't a human-interpretable answer. What matters is that the model found a basis where the coordinates are useful for its task.

In your interactive visualisation, play with rotating and scaling the basis. Watch coordinates change while points stay fixed. That intuition about the relativity of coordinates will serve you every time you work with embeddings, transforms, or learned representations.

Next, we'll dive into calculus concepts like derivatives and gradients, which tell us how functions change and are essential for training neural networks through backpropagation.
