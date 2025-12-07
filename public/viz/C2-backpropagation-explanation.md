# Backpropagation — Computing Gradients Layer by Layer

You've seen data flow forward through a network, transforming inputs into outputs. Now we reverse direction. Backpropagation sends error signals backward, computing exactly how much each weight contributed to the mistake. This is how neural networks learn.

---

## The Goal of Backpropagation

A neural network starts with random weights. It makes predictions, and those predictions are wrong. The question is: **how do we fix the weights?**

We need to know, for every single weight in the network:

> "If I nudge this weight up slightly, will the error go up or down? And by how much?"

Mathematically, we want **∂Loss/∂w** for every weight **w**. This is the partial derivative of the loss with respect to each weight—the gradient.

Once we have these gradients, we can adjust weights in the direction that reduces error. But computing them is the challenge. A network might have millions of weights. How do we efficiently compute millions of derivatives?

**Backpropagation** is the answer.

---

## Why Backwards?

Here's a key insight: we could compute gradients going forward, but it would be incredibly wasteful.

Imagine computing "how does weight w₁ affect the loss?" You'd trace w₁'s influence through every layer, through every neuron it touches, all the way to the output and loss. Then you'd do it again for w₂, and again for w₃, and so on. For each weight, you'd traverse the entire network.

**Backward is better.** Start at the loss and work backward. At each layer, you compute how the loss depends on that layer's outputs. Then you use that to compute how it depends on the layer's inputs and weights. One backward pass gives you gradients for ALL weights simultaneously.

This is called **reverse-mode automatic differentiation**, and it's the mathematical foundation of backpropagation.

Think of it like this: if you want to know how a river's source affects every downstream town, you could start at the source and trace every tributary. Or you could start at each town and trace back to the source—but that's inefficient if there are many towns. The backward approach traces from the final destination (the loss) back toward all sources (the weights) in one sweep.

---

## The Chain Rule Connection

Backpropagation is the chain rule, applied systematically.

Remember from calculus: if **y = f(g(x))**, then:

```
dy/dx = (dy/dg) × (dg/dx)
```

A neural network is just nested functions. Let's trace the dependencies:

```
Loss depends on → Output (y)
Output depends on → Pre-activation (z₂)
Pre-activation depends on → Hidden values (h) and Weights (W₂)
Hidden values depend on → Pre-activation (z₁)
Pre-activation depends on → Inputs (x) and Weights (W₁)
```

To find how Loss depends on W₁, we chain through every intermediate step:

```
∂Loss/∂W₁ = (∂Loss/∂y) × (∂y/∂z₂) × (∂z₂/∂h) × (∂h/∂z₁) × (∂z₁/∂W₁)
```

Each factor is a "local gradient"—how one quantity directly affects the next. Backprop computes these local gradients and multiplies them together as it moves backward.

---

## The Local Gradient

Every operation in a neural network has a local gradient—the derivative of its output with respect to its input.

Here are the local gradients for operations we'll encounter:

| Operation | Forward | Local Gradient (∂out/∂in) |
|-----------|---------|---------------------------|
| Weighted sum: z = wx + b | z = wx + b | ∂z/∂w = x, ∂z/∂x = w, ∂z/∂b = 1 |
| ReLU: h = max(0, z) | h = max(0, z) | 1 if z > 0, else 0 |
| Sigmoid: h = σ(z) | h = 1/(1+e⁻ᶻ) | h(1 - h) |
| MSE Loss: L = ½(y - t)² | L = ½(y - t)² | ∂L/∂y = (y - t) |

During the backward pass, each node receives a gradient from above (how the loss changes with its output) and multiplies by its local gradient to pass the signal backward.

---

## Step-by-Step Backpropagation

Let's walk through the backward pass conceptually before we crunch numbers.

### Step 1: Compute Loss Gradient

Start at the loss function. For Mean Squared Error with target **t** and prediction **y**:

```
∂Loss/∂y = (y - t)
```

This tells us: "For each unit the prediction is off, the loss changes by that amount."

### Step 2: Backprop Through Output Activation

The output **y** came from an activation function applied to **z₂**:

```
y = activation(z₂)
```

Using the chain rule:

```
∂Loss/∂z₂ = (∂Loss/∂y) × (∂y/∂z₂)
```

The second factor is the activation derivative. For sigmoid: **∂y/∂z₂ = y(1 - y)**

### Step 3: Compute Weight Gradients for Output Layer

The pre-activation **z₂** was computed as:

```
z₂ = W₂ · h + b₂
```

So:
- **∂z₂/∂W₂ = h** (the hidden layer values)
- **∂z₂/∂b₂ = 1**
- **∂z₂/∂h = W₂** (the weights, for passing gradient backward)

Weight gradient:
```
∂Loss/∂W₂ = (∂Loss/∂z₂) × h
```

Bias gradient:
```
∂Loss/∂b₂ = ∂Loss/∂z₂
```

### Step 4: Backprop to Hidden Layer

To continue backward, we need the gradient with respect to the hidden layer outputs:

```
∂Loss/∂h = (∂Loss/∂z₂) × W₂
```

### Step 5: Backprop Through Hidden Activation

The hidden values **h** came from activating **z₁**:

```
∂Loss/∂z₁ = (∂Loss/∂h) × (∂h/∂z₁)
```

For ReLU, **∂h/∂z₁** is 1 if z₁ > 0, else 0.

### Step 6: Compute Weight Gradients for Hidden Layer

Finally:
```
∂Loss/∂W₁ = (∂Loss/∂z₁) × x
∂Loss/∂b₁ = ∂Loss/∂z₁
```

We now have gradients for every weight and bias in the network.

---

## Gradient Accumulation

What happens when one neuron sends its output to multiple neurons in the next layer?

The gradients **add up**.

If hidden neuron h₁ feeds into both output neurons, the gradient flowing back to h₁ is the **sum** of gradients from both paths:

```
∂Loss/∂h₁ = (∂Loss/∂z₂₁) × w₁₁ + (∂Loss/∂z₂₂) × w₂₁
```

This is the multivariate chain rule in action. When a variable affects the output through multiple paths, you sum the contributions from each path.

---

## Worked Example with Numbers

Let's compute exact gradients for the network from our forward pass example.

### Network Recap (from C1)

**Architecture**: 2 inputs → 2 hidden neurons → 1 output

**Forward Pass Results** (with inputs x = [0.5, 0.8]):

| Layer | Pre-activation (z) | After Activation |
|-------|-------------------|------------------|
| Input | — | x = [0.5, 0.8] |
| Hidden | z₁ = [0.54, 0.20] | h = [0.54, 0.20] (ReLU) |
| Output | z₂ = [0.444] | y = [0.609] (Sigmoid) |

**Weights and Biases**:
```
W₁ = | 0.4   0.3 |    b₁ = [0.1, -0.1]
     |-0.2   0.5 |

W₂ = | 0.6  -0.4 |    b₂ = [0.2]
```

**Target**: Let's say the true label is **t = 1.0**

**Loss** (Mean Squared Error):
```
L = ½(y - t)² = ½(0.609 - 1.0)² = ½(-0.391)² = ½(0.153) = 0.0765
```

Now let's backpropagate!

---

### Backward Pass Step 1: Loss → Output

**Gradient of Loss with respect to y:**

```
∂L/∂y = (y - t) = 0.609 - 1.0 = -0.391
```

This is negative, meaning: to reduce loss, we need y to **increase** (since it's below the target).

---

### Backward Pass Step 2: Output Activation

**Gradient through sigmoid:**

The sigmoid derivative is **y(1 - y)**:

```
∂y/∂z₂ = y × (1 - y) = 0.609 × (1 - 0.609) = 0.609 × 0.391 = 0.238
```

**Chain rule to get ∂L/∂z₂:**

```
∂L/∂z₂ = (∂L/∂y) × (∂y/∂z₂)
       = (-0.391) × (0.238)
       = -0.093
```

---

### Backward Pass Step 3: Output Layer Weights

Recall: **z₂ = W₂ · h + b₂ = 0.6×h₁ + (-0.4)×h₂ + 0.2**

**Gradient for W₂:**

For the weight connecting h₁ to output (w = 0.6):
```
∂L/∂w₂₁ = (∂L/∂z₂) × (∂z₂/∂w₂₁)
        = (∂L/∂z₂) × h₁
        = (-0.093) × (0.54)
        = -0.050
```

For the weight connecting h₂ to output (w = -0.4):
```
∂L/∂w₂₂ = (∂L/∂z₂) × h₂
        = (-0.093) × (0.20)
        = -0.019
```

**Gradient for b₂:**
```
∂L/∂b₂ = ∂L/∂z₂ = -0.093
```

**Summary of output layer gradients:**
```
∂L/∂W₂ = [-0.050, -0.019]
∂L/∂b₂ = -0.093
```

---

### Backward Pass Step 4: Hidden Layer Values

**Gradient flowing back to hidden layer:**

```
∂L/∂h₁ = (∂L/∂z₂) × (∂z₂/∂h₁) = (-0.093) × (0.6) = -0.056
∂L/∂h₂ = (∂L/∂z₂) × (∂z₂/∂h₂) = (-0.093) × (-0.4) = 0.037
```

Note how h₂'s weight is negative (-0.4), so the gradient flips sign!

---

### Backward Pass Step 5: Hidden Activation (ReLU)

**Gradient through ReLU:**

ReLU derivative is 1 if z > 0, else 0.

Both z₁₁ = 0.54 and z₁₂ = 0.20 are positive, so ReLU passes gradients through unchanged:

```
∂L/∂z₁₁ = (∂L/∂h₁) × 1 = -0.056
∂L/∂z₁₂ = (∂L/∂h₂) × 1 = 0.037
```

If either pre-activation had been negative (and thus ReLU'd to zero), its gradient would be zero—the "dying ReLU" phenomenon.

---

### Backward Pass Step 6: Hidden Layer Weights

**Gradients for W₁:**

For h₁'s weights (first row of W₁):
```
∂L/∂w₁₁ = (∂L/∂z₁₁) × x₁ = (-0.056) × (0.5) = -0.028
∂L/∂w₁₂ = (∂L/∂z₁₁) × x₂ = (-0.056) × (0.8) = -0.045
```

For h₂'s weights (second row of W₁):
```
∂L/∂w₂₁ = (∂L/∂z₁₂) × x₁ = (0.037) × (0.5) = 0.019
∂L/∂w₂₂ = (∂L/∂z₁₂) × x₂ = (0.037) × (0.8) = 0.030
```

**Gradients for b₁:**
```
∂L/∂b₁₁ = ∂L/∂z₁₁ = -0.056
∂L/∂b₁₂ = ∂L/∂z₁₂ = 0.037
```

---

### Complete Gradient Summary

| Parameter | Value | Gradient (∂L/∂param) |
|-----------|-------|---------------------|
| w₁₁ (x₁ → h₁) | 0.4 | **-0.028** |
| w₁₂ (x₂ → h₁) | 0.3 | **-0.045** |
| w₂₁ (x₁ → h₂) | -0.2 | **+0.019** |
| w₂₂ (x₂ → h₂) | 0.5 | **+0.030** |
| b₁₁ | 0.1 | **-0.056** |
| b₁₂ | -0.1 | **+0.037** |
| w₂₁ (h₁ → y) | 0.6 | **-0.050** |
| w₂₂ (h₂ → y) | -0.4 | **-0.019** |
| b₂ | 0.2 | **-0.093** |

**Interpreting the gradients:**

- Negative gradients mean "increase this weight to reduce loss"
- Positive gradients mean "decrease this weight to reduce loss"
- Larger magnitude = this weight has more influence on the error

For example, w₁₂ has gradient -0.045. If we increase w₁₂, the loss will decrease. This makes sense: we want a higher output (to get closer to target 1.0), and increasing weights along the positive-valued path helps achieve that.

---

## The Weight Update (Preview of Gradient Descent)

With gradients computed, updating weights is simple:

```
w_new = w_old - learning_rate × gradient
```

If learning rate = 0.1:

```
w₁₂_new = 0.3 - (0.1 × -0.045) = 0.3 + 0.0045 = 0.3045
```

The weight increases slightly, nudging the network toward better predictions. Repeat this for all weights, run another forward pass, compute new gradients, update again. This is training.

---

## Why This Matters for ML/AI

### Backprop Enables Deep Learning

Without backpropagation, we couldn't train deep networks. Computing gradients by other methods (like finite differences) would require forward passes proportional to the number of weights—impossibly slow for networks with millions of parameters.

Backprop computes all gradients in roughly the same time as one forward pass. This efficiency unlocked modern deep learning.

### Automatic Differentiation

You rarely implement backprop manually. Libraries like PyTorch and TensorFlow implement **automatic differentiation**—they build a computational graph during the forward pass and automatically apply the chain rule backward.

When you write:
```python
loss.backward()  # PyTorch
```

The library traverses the graph in reverse, computing exactly the gradients we calculated manually.

### Understanding Helps Debugging

Even though it's automated, understanding backprop helps you:
- Debug vanishing/exploding gradients
- Understand why certain architectures train better
- Interpret gradient-based analysis (saliency maps, adversarial examples)
- Design custom layers with correct gradient computations

---

## Common Confusions

### Backprop ≠ Gradient Descent

**Backpropagation** computes gradients. It answers: "What is ∂Loss/∂w for each weight?"

**Gradient descent** uses those gradients to update weights. It's the optimization algorithm.

They work together, but they're distinct concepts. You could compute gradients with backprop and use a different optimizer (Adam, RMSprop, etc.) to update weights.

### Why Multiply, Not Add?

Some students wonder: "Why do we multiply gradients along the path instead of adding them?"

The chain rule requires multiplication. If f(x) = 2x and g(f) = 3f, then:
- A small change δ in x causes change 2δ in f
- That 2δ change in f causes change 3×2δ = 6δ in g

The effects **compound**, they don't just sum. The chain rule captures this compounding through multiplication.

We only **add** gradients when a single variable affects the loss through multiple independent paths (gradient accumulation).

### Gradients Flow Backward, Updates Happen Later

Don't confuse the backward pass with weight updates. During backprop, weights don't change—we're just computing gradients. The weights update afterward, typically after processing a batch of examples.

---

## Key Takeaways

1. **Backprop computes ∂Loss/∂w for every weight** in one backward pass
2. **Backward is efficient**: one pass gives all gradients, versus one pass per weight going forward
3. **It's the chain rule applied systematically**: multiply local gradients as you move backward
4. **Each operation has a local gradient**: the derivative of its output with respect to input
5. **Gradients accumulate (add) across multiple paths** from a single source
6. **Negative gradient means "increase weight"**; positive means "decrease weight"
7. **Autodiff libraries do this automatically**, but understanding helps debugging and architecture design

In your visualization, watch the gradients flow backward—starting at the loss, multiplying through each layer, accumulating at weights. Each colored path shows the chain rule in action, computing how the tiniest weight change would ripple forward to affect the final loss.

---

*Next: C3 — Weight Updates & Learning: How Gradient Descent Uses Backprop*
