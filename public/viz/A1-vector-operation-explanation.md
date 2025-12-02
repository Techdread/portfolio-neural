# Vector Operations: The Language of Neural Networks

## Intuitive Introduction — What Even Is a Vector?

Forget the abstract mathematics for a moment. A vector is simply **a quantity that has both a size and a direction**. That's it.

Think about the difference between these two statements:

- "I walked 5 kilometres" — this is a *scalar* (just a number)
- "I walked 5 kilometres north" — this is a *vector* (number + direction)

As a developer, you can think of a vector as an array of numbers like `[3, 4]` or `[1, 2, 5]`. But here's the key insight: those numbers aren't just arbitrary values sitting in memory. They represent *coordinates* that define an arrow pointing from the origin to that position.

The vector `[3, 4]` means: "Go 3 units in the x-direction, then 4 units in the y-direction." The arrow from `[0, 0]` to `[3, 4]` *is* the vector.

**Real-world vector examples:**

- **Velocity**: A car moving at 60 km/h *eastward* (speed + direction)
- **Force**: Pushing a box with 10 newtons of force *to the right*
- **Displacement**: Your destination is 500 metres away, *bearing northeast*

Every vector has two properties:

1. **Magnitude** (length): How "big" is it? For `[3, 4]`, the magnitude is 5 (using the Pythagorean theorem: √(3² + 4²) = 5)
2. **Direction**: Where does it point?

When you look at the visualization, notice how the arrow's length corresponds to the magnitude, and the arrow's angle shows the direction.

---

## Vector Addition & Subtraction — Combining Movements

### Addition: The "Tip-to-Tail" Method

Imagine you're giving someone directions: "Walk 3 blocks east, then walk 4 blocks north." Where do they end up? Vector addition answers exactly this question.

To add two vectors **a** and **b**:

1. Place the tail (start) of **b** at the tip (end) of **a**
2. Draw a new vector from the tail of **a** to the tip of **b**
3. That new vector is your result: **a** + **b**

**Worked example:**

```
a = [3, 1]  // 3 right, 1 up
b = [1, 3]  // 1 right, 3 up

a + b = [3+1, 1+3] = [4, 4]  // 4 right, 4 up total
```

In code terms, vector addition is just element-wise addition:

```javascript
const add = (a, b) => a.map((val, i) => val + b[i]);
```

The beautiful thing is that **order doesn't matter**. Adding **a** then **b** gets you to the same place as adding **b** then **a**. Drag the vectors in the visualization to see this for yourself.

### Subtraction: Finding the Difference

Vector subtraction answers a different question: "What's the displacement *from* point A *to* point B?"

**a** - **b** gives you the vector you'd need to add to **b** to reach **a**.

```
a = [5, 3]
b = [2, 1]

a - b = [5-2, 3-1] = [3, 2]
```

Think of it this way: if you're at position **b** and want to get to position **a**, you need to travel by vector (**a** - **b**).

---

## Scalar Multiplication — Stretching and Shrinking

A **scalar** is just a fancy word for a regular number (not a vector). When you multiply a vector by a scalar, you're scaling its magnitude without changing its direction (usually).

```
v = [2, 3]

2 * v = [4, 6]    // twice as long, same direction
0.5 * v = [1, 1.5] // half as long, same direction
```

**Key insights:**

- Scalar > 1: The vector stretches (gets longer)
- Scalar between 0 and 1: The vector shrinks
- Scalar = 0: The vector becomes `[0, 0]` (the zero vector)
- **Negative scalar**: The vector flips direction *and* scales

That last point is crucial. Multiplying by -1 doesn't just negate the numbers—it reverses the vector's direction:

```
v = [3, 2]
-1 * v = [-3, -2]  // Points the opposite way!
```

In code:

```javascript
const scale = (scalar, v) => v.map(val => scalar * val);
```

Watch the visualization as you adjust the scalar slider. Notice how the arrow stretches, shrinks, and flips.

---

## The Dot Product — Measuring Alignment

The dot product is where vectors become genuinely powerful for AI/ML. It's a way of multiplying two vectors to get a single number (a scalar) that tells you something profound: **how much do these vectors point in the same direction?**

### Interpretation 1: The Algebraic Formula

The dot product is computationally simple. Multiply corresponding components and sum the results:

```
a = [2, 3]
b = [4, 1]

a · b = (2×4) + (3×1) = 8 + 3 = 11
```

For 3D vectors:

```
a = [1, 2, 3]
b = [4, 5, 6]

a · b = (1×4) + (2×5) + (3×6) = 4 + 10 + 18 = 32
```

In code, this is a classic reduce operation:

```javascript
const dot = (a, b) => a.reduce((sum, val, i) => sum + val * b[i], 0);
```

### Interpretation 2: Geometric Projection

Geometrically, the dot product tells you how much one vector "goes in the direction" of another. Imagine shining a light perpendicular to vector **b**—the dot product relates to the length of **a**'s shadow on **b**.

More precisely: **a** · **b** = |**a**| × |**b**| × cos(θ), where θ is the angle between them.

### Interpretation 3: Similarity Measure

This is the interpretation that makes the dot product indispensable for AI:

- **Positive dot product**: Vectors point in *similar* directions (angle < 90°)
- **Zero dot product**: Vectors are *perpendicular* (angle = 90°) — completely independent
- **Negative dot product**: Vectors point in *opposite* directions (angle > 90°)

The larger the positive value, the more aligned the vectors are. The larger the negative value, the more opposed they are.

**Quick reference:**

| Dot Product | Meaning | Angle |
|-------------|---------|-------|
| Large positive | Very similar direction | Small (close to 0°) |
| Zero | Perpendicular, unrelated | Exactly 90° |
| Large negative | Opposite directions | Large (close to 180°) |

Play with the visualization—drag the vectors and watch how the dot product changes as they align or oppose each other.

---

## Why This Matters for ML/AI

Here's where everything clicks together. The operations you've just learned aren't abstract mathematics—they're the fundamental computations happening billions of times in every neural network.

### 1. Neurons Compute Dot Products

A single neuron does exactly one thing: it computes the dot product of its inputs and weights, then applies an activation function.

```
inputs  = [0.5, 0.3, 0.8]   // Your data
weights = [0.2, 0.9, 0.1]   // Learned parameters

weighted_sum = inputs · weights
             = (0.5×0.2) + (0.3×0.9) + (0.8×0.1)
             = 0.1 + 0.27 + 0.08
             = 0.45
```

That weighted sum is literally a dot product. When we say a neural network "learns," we mean it's adjusting those weight vectors so that the dot products produce useful outputs.

### 2. Embeddings and Similarity

Modern AI systems convert words, images, and concepts into vectors called **embeddings**. The word "king" might become a 300-dimensional vector. The word "queen" becomes another vector.

How do we measure if two words are related? **Dot product** (or its normalised cousin, cosine similarity).

```
similarity = embedding("king") · embedding("queen")  // High value!
similarity = embedding("king") · embedding("banana")  // Low value
```

This is how search engines find relevant documents, how recommendation systems suggest similar items, and how chatbots understand that "happy" and "joyful" mean similar things.

### 3. Attention Mechanisms (Transformers)

The transformer architecture—the foundation of GPT, Claude, and other large language models—relies entirely on dot products. The "attention" mechanism works by:

1. Creating query, key, and value vectors for each word
2. Computing dot products between queries and keys to determine "which words should pay attention to which other words"
3. Using those attention scores to create weighted sums (vector addition and scalar multiplication)

Every time you interact with an AI assistant, trillions of dot products are being computed to determine which context is relevant to your question.

---

## Mathematical Notation

Now that you understand the concepts, here's the notation you'll encounter in papers and textbooks:

**Representing vectors:**

- **Bold lowercase letters**: **v**, **a**, **b**, **w**
- **Arrow notation**: v⃗, a⃗, b⃗ (common in physics)
- **Component form**: v = [v₁, v₂, v₃] or v = (v₁, v₂, v₃)
- **Column vectors**: Written vertically in matrices (you'll see this in linear algebra)

**Operations:**

- **Addition**: **a** + **b** or a⃗ + b⃗
- **Scalar multiplication**: c**v** or cv⃗ (where c is a scalar)
- **Dot product**: **a** · **b** or **a**ᵀ**b** or ⟨**a**, **b**⟩
- **Magnitude/length**: |**v**| or ‖**v**‖

**Common conventions:**

- **x̂**, **ŷ**, **ẑ**: Unit vectors (length = 1) along each axis
- **0**: The zero vector [0, 0, ...] — has no direction
- **n**: Often denotes the number of dimensions

---

## Common Pitfalls

As a developer coming to vectors, watch out for these frequent mistakes:

### 1. Confusing Points and Vectors

A point `(3, 4)` is a location. A vector `[3, 4]` is a displacement. They look identical but mean different things. The vector `[3, 4]` can be placed anywhere—it represents "go 3 right and 4 up" regardless of where you start.

### 2. Forgetting That Dot Products Return Scalars

```javascript
// WRONG mental model:
const result = dot([1,2], [3,4]);  // result is NOT a vector!

// CORRECT:
const result = dot([1,2], [3,4]);  // result = 11 (a single number)
```

Vectors in, scalar out. Always.

### 3. Mixing Up Dot Product and Element-wise Multiplication

```javascript
// Element-wise (Hadamard) product:
[2, 3] * [4, 5] = [8, 15]  // Still a vector

// Dot product:
[2, 3] · [4, 5] = 8 + 15 = 23  // A scalar
```

Both are valid operations, but they do completely different things.

### 4. Assuming Zero Dot Product Means "Zero Similarity"

Zero doesn't mean "unrelated" in a bad way—it means the vectors are perfectly perpendicular, which is actually meaningful information. Truly "unrelated" vectors in high dimensions tend to have dot products close to zero, but not exactly zero.

### 5. Ignoring Magnitude When Measuring Similarity

If you just use the dot product for similarity, longer vectors will always seem "more similar" to everything. That's why we often use **cosine similarity**, which normalises by magnitude:

```
cosine_similarity = (a · b) / (|a| × |b|)
```

This gives you a value between -1 and 1, purely based on direction.

---

## Wrapping Up

You've now learned the core vector operations that power modern AI:

- **Vectors** represent quantities with magnitude and direction
- **Addition** combines movements (tip-to-tail)
- **Subtraction** finds the displacement between points
- **Scalar multiplication** stretches, shrinks, or flips vectors
- **Dot products** measure alignment and compute weighted sums

These aren't just mathematical curiosities. Every neural network, every embedding model, every attention mechanism is built on these foundations. When you understand vectors intuitively, you understand the language that AI speaks.

Use the interactive visualization to build your intuition. Drag vectors around. Watch the numbers change. There's no substitute for seeing these operations in action.

*Next up: Matrix operations — what happens when we work with many vectors at once.*