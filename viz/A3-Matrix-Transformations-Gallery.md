# Matrix Transformations: Composition and Order Effects

You've learned that matrices transform space and that multiplying matrices combines their effects. Now let's build a proper toolkit. This section is your reference guide to the standard transformation matrices, and more importantly, how to chain them together to build complex transformations from simple parts.

The interactive visualization will let you stack transformations and watch what happens when you swap the order. Spoiler: the results are often dramatically different.


## 1. The Transformation Zoo

Here's your field guide to the transformation matrices you'll encounter repeatedly in graphics, games, robotics, and yes, neural networks. Keep this section bookmarked.

**Identity Matrix — The "do nothing" transform**

```typescript
// 2D Identity
const I_2D = [
  [1, 0],
  [0, 1]
];

// 3D Identity
const I_3D = [
  [1, 0, 0],
  [0, 1, 0],
  [0, 0, 1]
];
```

Multiplying by identity returns the input unchanged. It's the matrix equivalent of multiplying by 1.


**Scaling — Stretch or squash along axes**

```typescript
// 2D Scaling by factors sx, sy
const scale2D = (sx: number, sy: number) => [
  [sx, 0],
  [0, sy]
];

// Uniform scaling (same factor everywhere)
const uniformScale = (s: number) => scale2D(s, s);

// 3D Scaling
const scale3D = (sx: number, sy: number, sz: number) => [
  [sx, 0,  0],
  [0,  sy, 0],
  [0,  0,  sz]
];
```

When sx = sy, objects scale uniformly (like zooming). When they differ, you get stretching or squashing along specific axes.


**Rotation — Spin around the origin**

```typescript
// 2D Rotation by angle θ (counterclockwise)
const rotate2D = (theta: number) => [
  [Math.cos(theta), -Math.sin(theta)],
  [Math.sin(theta),  Math.cos(theta)]
];

// 3D Rotation around X axis
const rotateX = (theta: number) => [
  [1, 0,              0],
  [0, Math.cos(theta), -Math.sin(theta)],
  [0, Math.sin(theta),  Math.cos(theta)]
];

// 3D Rotation around Y axis
const rotateY = (theta: number) => [
  [Math.cos(theta),  0, Math.sin(theta)],
  [0,               1, 0],
  [-Math.sin(theta), 0, Math.cos(theta)]
];

// 3D Rotation around Z axis
const rotateZ = (theta: number) => [
  [Math.cos(theta), -Math.sin(theta), 0],
  [Math.sin(theta),  Math.cos(theta), 0],
  [0,               0,              1]
];
```

Notice each 3D rotation matrix leaves one axis unchanged (the axis you're rotating around) while applying the 2D rotation formula to the other two.


**Shearing — Skew space**

```typescript
// 2D Shear along X (points slide horizontally based on their y)
const shearX = (k: number) => [
  [1, k],
  [0, 1]
];

// 2D Shear along Y (points slide vertically based on their x)
const shearY = (k: number) => [
  [1, 0],
  [k, 1]
];
```

Shearing turns rectangles into parallelograms. It's less common in ML but appears in data augmentation and some geometric deep learning applications.


**Reflection — Mirror across an axis**

```typescript
// Reflect across Y axis (flip horizontally)
const reflectY = [
  [-1, 0],
  [0,  1]
];

// Reflect across X axis (flip vertically)
const reflectX = [
  [1,  0],
  [0, -1]
];

// Reflect across origin (flip both)
const reflectOrigin = [
  [-1, 0],
  [0, -1]
];
```

Reflections have a determinant of -1, which means they flip the "handedness" of space. A clockwise loop becomes counterclockwise.


**Translation — Move without rotating** *(Requires homogeneous coordinates; see Section 5)*

```typescript
// 2D Translation (using 3×3 homogeneous matrix)
const translate2D = (tx: number, ty: number) => [
  [1, 0, tx],
  [0, 1, ty],
  [0, 0, 1]
];

// 3D Translation (using 4×4 homogeneous matrix)
const translate3D = (tx: number, ty: number, tz: number) => [
  [1, 0, 0, tx],
  [0, 1, 0, ty],
  [0, 0, 1, tz],
  [0, 0, 0, 1]
];
```


## 2. Composition: Combining Transformations

Here's the magic: to apply multiple transformations in sequence, you multiply their matrices together. The result is a single matrix that does everything at once.

```typescript
// Scale by 2, then rotate 45°
const scaleMatrix = scale2D(2, 2);
const rotateMatrix = rotate2D(Math.PI / 4);

// Combined transformation
const combined = matmul(rotateMatrix, scaleMatrix);

// Now 'combined' does both operations in one multiplication
const result = matmul(combined, point);
```

Why is this powerful? Because no matter how many transformations you chain, the result is always just one matrix. A hundred transformations? Still just one matrix multiplication at runtime. This is exactly how graphics pipelines work, and it's analogous to how neural networks collapse many learned transformations into efficient forward passes.


## 3. Order Matters: A Visual Proof

This is the most important intuition in this entire section.

Consider two simple operations: rotate 90° and translate right by 5 units.

**Scenario A: Rotate first, then translate**

Start with a point at (1, 0). Rotate 90° counterclockwise: it moves to (0, 1). Now translate right by 5: it ends at (5, 1).

**Scenario B: Translate first, then rotate**

Start with the same point at (1, 0). Translate right by 5: it moves to (6, 0). Now rotate 90° around the origin: it swings up to (0, 6).

Final positions: (5, 1) versus (0, 6). Completely different results from the same two operations in different order.

```
Scenario A: Rotate then Translate
    (1,0) --rotate--> (0,1) --translate--> (5,1)

Scenario B: Translate then Rotate  
    (1,0) --translate--> (6,0) --rotate--> (0,6)
```

The interactive visualization makes this visceral. You'll see an object take completely different paths depending on transformation order.


## 4. Reading Order Convention

Matrix multiplication reads **right to left** when thinking about transformation order.

If you write:
```typescript
const M = A * B * C;
const result = M * v;
```

The transformations apply as: **C first, then B, then A**.

This feels backwards at first, but it matches how function composition works: f(g(h(x))) applies h first, then g, then f. The innermost operation happens first.

```typescript
// "Translate, then rotate, then scale" is written as:
const M = Scale * Rotate * Translate;

// When applied to vector v:
// 1. Translate is applied first
// 2. Rotate is applied to that result
// 3. Scale is applied last
```

Many graphics libraries (including Three.js) handle this for you with method chaining that reads in the intuitive order. But when you're debugging matrix math or reading shader code, remember: rightmost matrix acts first.


## 5. Homogeneous Coordinates

Here's a problem: translation isn't a linear transformation. You can't represent "add 5 to x" as a 2×2 matrix multiplication. Scaling and rotation work because they're centered on the origin, but translation moves the origin itself.

The solution is elegant: add an extra dimension.

**The trick:** Represent 2D points as 3D vectors with a 1 in the third position.

```typescript
// 2D point (x, y) becomes homogeneous (x, y, 1)
const point2D = [3, 4];
const pointHomogeneous = [3, 4, 1];
```

Now translation works as matrix multiplication:

```typescript
const translate = [
  [1, 0, 5],   // x' = x + 5
  [0, 1, 3],   // y' = y + 3
  [0, 0, 1]    // 1' = 1 (unchanged)
];

// [3, 4, 1] × translate = [8, 7, 1]
// Which represents point (8, 7)
```

For 3D graphics, we use 4×4 matrices with 4D homogeneous coordinates. This is why every 3D graphics API (OpenGL, DirectX, Three.js) uses 4×4 matrices even for 3D transformations.

**Bonus insight:** The extra dimension also enables perspective projection (things getting smaller with distance), which is why it's universal in 3D graphics.


## 6. Why This Matters for ML/AI

Understanding transformation composition directly maps to understanding neural networks.

**Neural networks stack transformations.** Each layer is a transformation of the input space. A deep network is a composition of many transformations, just like chaining matrices:

```
Input → Layer1 → Layer2 → Layer3 → Output
        (W1)      (W2)     (W3)
        
Equivalent to: Output = W3 × W2 × W1 × Input
```

**Feature space warping.** When you visualize what a neural network learns, you're seeing how it warps feature space. Early layers might do something like rotation and scaling (separating obvious features), while later layers do more complex, nonlinear warping (thanks to activation functions).

**Data augmentation uses these exact transformations.** Training image classifiers? You're probably randomly applying rotations, scales, translations, and shears to training images. Understanding these matrices helps you implement augmentation correctly and debug when images look wrong.

**Order matters in networks too.** BatchNorm before activation or after? Dropout before the dense layer or after? These ordering decisions affect what transformation the network learns, just like matrix multiplication order affects the result.

**Debugging shape issues.** When you understand that each layer transforms dimensions in a predictable way, you can trace through a network and predict shapes at each stage. The composition rules are the same as matrix multiplication compatibility rules.


## 7. Building Complex Transforms

Let's put it together with a classic problem: **rotate around an arbitrary point**, not the origin.

The naive rotation matrix rotates around (0, 0). But what if you want to rotate a shape around its own center at point (cx, cy)?

**The recipe:**
1. Translate so the center moves to the origin
2. Rotate around the origin
3. Translate back to the original position

```typescript
const rotateAroundPoint = (
  theta: number, 
  cx: number, 
  cy: number
) => {
  const toOrigin = translate2D(-cx, -cy);
  const rotate = rotate2DHomogeneous(theta);
  const backToPosition = translate2D(cx, cy);
  
  // Remember: rightmost applies first
  // So: toOrigin first, then rotate, then backToPosition
  return matmul(backToPosition, matmul(rotate, toOrigin));
};
```

This pattern appears everywhere: move to a convenient reference frame, do your operation, move back. In 3D graphics, this is how you rotate an object around its local axis rather than the world axis. In robotics, it's how you compute joint movements.

**Other composite transforms you'll encounter:**

Reflect across an arbitrary line: translate line to origin, rotate to align with axis, reflect, rotate back, translate back.

Scale from a specific point: translate point to origin, scale, translate back.

Look-at matrix (camera pointing at target): combination of translation and rotation that's fundamental to 3D rendering.

Each of these breaks down into a sequence of simple transforms, multiplied together in the right order.


## Wrapping Up

You now have a toolkit of standard transformations and the knowledge to combine them. The key insights are that matrices chain through multiplication, order matters dramatically, and homogeneous coordinates let us include translation in the matrix framework.

In your Three.js visualization, experiment freely. Stack transformations, swap their order, and watch the results. That intuition about how transformations compose will serve you well whether you're debugging a graphics pipeline, implementing data augmentation, or reasoning about what a neural network layer is doing to your feature space.

Next, we'll look at what matrices can tell us about themselves through eigenvalues and eigenvectors, which reveals the "preferred directions" of any transformation.
