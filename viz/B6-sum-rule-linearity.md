# B6: Sum Rule & Linearity — The Derivative's Best Behavior

## Adding Functions: Stacking Heights

Before diving into rules, let's be clear about what it means to add functions.

When we write **h(x) = f(x) + g(x)**, we're saying: "At every x, add the height of f to the height of g."

For example, if f(x) = x² and g(x) = sin(x), then:

h(x) = x² + sin(x)

At x = 2: h(2) = 4 + sin(2) ≈ 4.91

The graph of h is literally the graphs of f and g stacked on top of each other. Every point on h is the sum of the corresponding points on f and g.

---

## The Sum Rule

Here's the good news: **differentiating sums is exactly as simple as you'd hope.**

### The Rule

For h(x) = f(x) + g(x):

**h'(x) = f'(x) + g'(x)**

Or more compactly:

**(f + g)' = f' + g'**

That's it. Differentiate each piece, then add the results.

### The Intuition: Slopes Add Up

Think about what a derivative measures — the rate of change, or slope.

If you're walking along h(x) = f(x) + g(x), your height is changing for two reasons:
- f is changing at rate f'(x)
- g is changing at rate g'(x)

Your total rate of change is simply the sum of these individual rates.

**Concrete example:** Imagine f is increasing at 2 units per second, and g is increasing at 3 units per second. How fast is h = f + g increasing? Obviously 5 units per second. The rates just add.

### Quick Example

Differentiate h(x) = x³ + eˣ

- d/dx[x³] = 3x²
- d/dx[eˣ] = eˣ

Therefore: **h'(x) = 3x² + eˣ**

No tricks, no complications. Just differentiate and add.

---

## The Constant Multiple Rule

What if you scale a function by a constant?

### The Rule

For h(x) = c · f(x), where c is a constant:

**h'(x) = c · f'(x)**

Or:

**(cf)' = c · f'**

Constants "pass through" the derivative unchanged.

### The Intuition: Scaling Steepness

If you double a function, you double its steepness everywhere.

Think of it graphically: h(x) = 2f(x) stretches f vertically by a factor of 2. Every slope gets twice as steep. A slope of 3 becomes 6. A slope of -1 becomes -2.

**Example:** If f(x) = sin(x), then f'(x) = cos(x).

For h(x) = 5·sin(x):
- h'(x) = 5·cos(x)

The 5 just comes along for the ride.

### Special Case: Negatives

What about h(x) = -f(x)? This is just c = -1:

**(-f)' = -f'**

Negating a function negates its derivative. Uphill becomes downhill, downhill becomes uphill.

---

## The Difference Rule

With the sum rule and the constant multiple rule, we get the difference rule for free:

**(f - g)' = f' - g'**

Why? Because f - g is really f + (-1)·g:

(f - g)' = (f + (-1)·g)' = f' + (-1)·g' = f' - g'

**Example:** Differentiate h(x) = x⁴ - cos(x)

- d/dx[x⁴] = 4x³
- d/dx[cos(x)] = -sin(x)

Therefore: h'(x) = 4x³ - (-sin(x)) = **4x³ + sin(x)**

---

## Linearity: The Big Picture

The sum rule and constant multiple rule combine into one powerful property called **linearity**.

### The Linear Combination Rule

For any constants a and b:

**d/dx[a·f(x) + b·g(x)] = a·f'(x) + b·g'(x)**

This extends to any number of terms:

**d/dx[a₁f₁ + a₂f₂ + ... + aₙfₙ] = a₁f₁' + a₂f₂' + ... + aₙfₙ'**

### What "Linear Operator" Means

Mathematicians say the derivative is a **linear operator**. This means it satisfies two properties:

1. **Additivity:** (f + g)' = f' + g'
2. **Homogeneity:** (cf)' = c · f'

Any operation satisfying both is linear. The derivative behaves "nicely" — it respects the structure of addition and scaling.

Not all operations are linear! For example, squaring is not linear: (f + g)² ≠ f² + g². But differentiation is, and that makes calculus vastly more manageable.

---

## Why This is Wonderful

Linearity is what makes differentiation tractable. Here's the practical payoff:

### Break It Down, Build It Up

You can decompose any polynomial (or sum of functions) into pieces:

h(x) = 3x⁴ - 2x² + 7x - 5

Differentiate each term separately:
- d/dx[3x⁴] = 12x³
- d/dx[-2x²] = -4x
- d/dx[7x] = 7
- d/dx[-5] = 0

Combine: **h'(x) = 12x³ - 4x + 7**

No matter how long the sum, you just handle each piece independently.

### Constants Vanish

Notice that d/dx[-5] = 0. The derivative of any constant is zero — constants don't change, so their rate of change is zero. This falls out naturally: if f(x) = c, then f'(x) = 0.

### Complex Functions Become Simple

Any function that's a sum of "basic" functions (polynomials, trig functions, exponentials) can be differentiated term by term. You only need to memorize derivatives of the basic building blocks; linearity handles the assembly.

---

## Why This Matters for ML/AI

Linearity isn't just convenient for homework — it's fundamental to how neural networks learn.

### Neural Networks Are Sums

A basic neuron computes:

**output = w₁x₁ + w₂x₂ + ... + wₙxₙ + b**

This is a weighted sum — exactly the kind of expression where linearity shines. When computing gradients, each term contributes independently.

### Gradients Distribute Over Addition

During backpropagation, when you hit an addition node:

```
z = x + y
```

The gradient flows through unchanged to both inputs:

```
∂L/∂x = ∂L/∂z
∂L/∂y = ∂L/∂z
```

This is the sum rule in action. The upstream gradient copies directly to both branches. No transformation, no scaling — addition just passes gradients through.

### Sum Nodes Are "Free" in Backprop

Computationally, sum nodes are trivial during backpropagation. Compare:
- **Multiplication:** Requires the product rule — gradient depends on *both* inputs
- **Addition:** Gradient just copies through — no computation needed

This is why sums in neural networks don't complicate gradient flow.

### Residual Connections: The Secret Weapon

ResNets (Residual Networks) revolutionized deep learning with a simple idea:

**output = F(x) + x**

Instead of learning a transformation F(x), learn a *residual* F(x) and add it to the input.

Why does this help? Linearity. The gradient with respect to x flows through two paths:
1. Through F(x) — may be complex, may vanish
2. Through the direct connection (+x) — **always passes through unchanged**

That "+x" creates a gradient superhighway. Even if F's gradients vanish, the identity path preserves gradient flow. This is why ResNets can train hundreds of layers deep while plain networks fail at 20 layers.

The sum rule guarantees this works: (F(x) + x)' includes a term for x that doesn't depend on F at all.

---

## Summary

**Sum Rule:** (f + g)' = f' + g' — differentiate and add.

**Constant Multiple Rule:** (cf)' = c · f' — constants pass through.

**Difference Rule:** (f - g)' = f' - g' — follows from above.

**Linearity:** d/dx[af + bg] = af' + bg' — the derivative respects linear combinations.

**Why it matters:**
- Break complex functions into simple pieces
- Differentiate each piece independently  
- Combine the results

**In ML:** Gradients distribute over sums effortlessly. Addition nodes in neural networks pass gradients through unchanged. Residual connections exploit this to enable training of extremely deep networks.

---

## What's Next?

You now have the tools to differentiate sums, products, and scaled functions. But what about *compositions* — functions inside other functions like sin(x²) or e^(3x)? That's the Chain Rule, the most important rule for machine learning and the key to understanding backpropagation.
