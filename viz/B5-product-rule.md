# B5: The Product Rule — Derivatives of Multiplied Functions

## The Setup: When Functions Multiply

You've learned to differentiate single functions like x², sin(x), and eˣ. But what happens when two functions are *multiplied together*?

Consider a function like:

**h(x) = f(x) · g(x)**

For example:
- h(x) = x² · sin(x)
- h(x) = eˣ · x
- h(x) = (x + 1) · (x² - 3)

Each of these is the *product* of two simpler functions. To find h'(x), we need a new rule.

---

## Why Not Just Multiply Derivatives?

Here's the trap that catches nearly everyone at first: "If h(x) = f(x) · g(x), surely h'(x) = f'(x) · g'(x)?"

**Let's test this with a simple example.**

Take h(x) = x · x = x²

We *know* the derivative of x² is 2x. That's our ground truth.

Now, let's try the "just multiply derivatives" approach:
- f(x) = x, so f'(x) = 1
- g(x) = x, so g'(x) = 1
- "Multiply derivatives": 1 × 1 = 1

But wait — we said h'(x) should be 2x, not 1!

**The "multiply derivatives" approach is completely wrong.** This isn't a small error; we got 1 instead of 2x. The discrepancy grows dramatically with more complex functions.

So what's actually happening when we differentiate a product?

---

## The Rectangle Analogy: Seeing the Product Rule

This is the key insight that makes the product rule intuitive. **Think of f(x) · g(x) as the area of a rectangle.**

Imagine a rectangle where:
- **Width** = f(x)
- **Height** = g(x)
- **Area** = f(x) · g(x)

Now, here's the crucial question: *When x changes slightly, how does the area change?*

### Both Dimensions Change Simultaneously

When x increases by a tiny amount Δx:
- The width changes from f(x) to f(x) + Δf
- The height changes from g(x) to g(x) + Δg

The new area is (f + Δf)(g + Δg). Let's expand this:

**(f + Δf)(g + Δg) = fg + f·Δg + g·Δf + Δf·Δg**

The change in area is:

**ΔArea = f·Δg + g·Δf + Δf·Δg**

This gives us three pieces:

1. **f · Δg** — A horizontal strip: keeping width f, height increases by Δg
2. **g · Δf** — A vertical strip: keeping height g, width increases by Δf  
3. **Δf · Δg** — A tiny corner: both changes together

### The Vanishing Corner

Here's the beautiful part. That corner piece (Δf · Δg) is *tiny squared* — it's the product of two infinitesimally small quantities. As Δx → 0, this term vanishes much faster than the others.

When we take the limit (which is what a derivative is), the corner disappears entirely:

**d(fg) = f·dg + g·df**

Dividing through by dx:

**d(fg)/dx = f · (dg/dx) + g · (df/dx)**

---

## The Product Rule Formula

### The Standard Form

For h(x) = f(x) · g(x):

**h'(x) = f'(x) · g(x) + f(x) · g'(x)**

Or equivalently:

**(fg)' = f'g + fg'**

### Leibniz Notation

Using Leibniz's notation with u and v:

**d(uv) = u·dv + v·du**

This is elegant because it shows the symmetry — each function gets its turn being differentiated while the other stays put.

### The Mnemonic

There's a classic memory aid:

> "**First times derivative of second, plus second times derivative of first.**"

Or more rhythmically:

> "**Left d-right, plus right d-left.**"

Think of it as giving each function a "turn" to be differentiated while its partner holds steady. The final answer adds both scenarios together.

---

## Worked Examples

### Example 1: h(x) = x² · sin(x)

**Identify the parts:**
- f(x) = x² → f'(x) = 2x
- g(x) = sin(x) → g'(x) = cos(x)

**Apply the product rule:**

h'(x) = f'(x) · g(x) + f(x) · g'(x)  
h'(x) = 2x · sin(x) + x² · cos(x)

**Final answer: h'(x) = 2x·sin(x) + x²·cos(x)**

You can factor out x if you like: h'(x) = x(2·sin(x) + x·cos(x))

### Example 2: h(x) = eˣ · x

**Identify the parts:**
- f(x) = eˣ → f'(x) = eˣ (the exponential's derivative is itself!)
- g(x) = x → g'(x) = 1

**Apply the product rule:**

h'(x) = eˣ · x + eˣ · 1  
h'(x) = eˣ · x + eˣ

**Final answer: h'(x) = eˣ(x + 1)**

We factored out eˣ to get a cleaner form. Notice how the derivative "remembers" both the original product *and* adds a new term.

### Example 3: Three Functions (Extended Product Rule)

What about h(x) = f(x) · g(x) · k(x)?

The pattern extends naturally. Each function takes a turn being differentiated:

**(fgk)' = f'gk + fg'k + fgk'**

The rule generalizes: for n functions multiplied together, you get n terms, each with exactly one function differentiated.

---

## Common Mistakes to Avoid

### Mistake 1: Multiplying the Derivatives

❌ **Wrong:** (fg)' = f' · g'

✅ **Right:** (fg)' = f'g + fg'

We proved this fails with h(x) = x · x above. Always add the two terms.

### Mistake 2: Forgetting One Term

Some students remember to differentiate one function but forget the second term entirely.

❌ **Wrong:** (x² · sin(x))' = 2x · cos(x)

✅ **Right:** (x² · sin(x))' = 2x · sin(x) + x² · cos(x)

Always count your terms. Product rule = two terms. Three functions = three terms.

### Mistake 3: Confusing Product Rule with Chain Rule

The product rule handles **f(x) · g(x)** — two separate functions multiplied.

The chain rule (coming later) handles **f(g(x))** — one function *inside* another.

These are different situations requiring different rules.

---

## Why This Matters for ML/AI

The product rule isn't just calculus trivia — it's essential for understanding how neural networks learn. Here's where you'll encounter it:

### Gating Mechanisms in LSTMs

Long Short-Term Memory networks use **gates** that multiply signals together:

**output = sigmoid(weights) × hidden_state**

When backpropagation computes gradients through this multiplication, it applies the product rule. The gradient flows through *both* the sigmoid path and the hidden state path, then sums them — exactly as the product rule prescribes.

### Attention Mechanisms

In attention layers (the heart of Transformers):

**output = softmax(scores) × values**

The attention weights (softmax output) multiply the values. During training, gradients must flow backward through this product. The product rule tells us the gradient splits into two paths: one through the attention weights, one through the values.

### Loss Functions with Regularization

Many loss functions combine multiple terms:

**total_loss = data_loss × weight_decay_factor**

Or use multiplicative scaling:

**weighted_loss = sample_weight × cross_entropy**

Computing gradients through these products requires the product rule.

### The Backpropagation Connection

When an automatic differentiation system (PyTorch, TensorFlow, JAX) encounters a multiplication node during backpropagation, it implements the product rule automatically:

```
Forward:  z = x * y
Backward: ∂L/∂x = y * (∂L/∂z)
          ∂L/∂y = x * (∂L/∂z)
```

Each input's gradient is the *other* input times the upstream gradient. This is the product rule in action — the gradient with respect to x involves y (the "other" function), and vice versa.

---

## Summary

**The Product Rule:** When differentiating h(x) = f(x) · g(x):

**h'(x) = f'(x) · g(x) + f(x) · g'(x)**

**The Rectangle Intuition:** Area changes because *both* dimensions change. The total change is the sum of the horizontal strip (f · Δg) plus the vertical strip (g · Δf). The corner (Δf · Δg) vanishes in the limit.

**The Mnemonic:** "First times derivative of second, plus second times derivative of first."

**In ML:** Every multiplication in a neural network — gating, attention, weighted losses — requires the product rule during backpropagation. The gradient splits and flows through both multiplicands.

---

## What's Next?

Now that you can handle products, what about *quotients* — one function divided by another? That's the Quotient Rule, which builds directly on what you've learned here. And after that, the Chain Rule will show you how to differentiate *compositions* of functions — the most powerful (and most used) rule in all of machine learning.
