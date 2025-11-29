# The Chain Rule

*Derivatives of Composed Functions*

## 1. Function Composition: The Pipeline

Before we tackle the chain rule, let's make sure we're solid on function composition. When you write f(g(x)), you're describing a two-step process:

1. First, g takes x and produces some output
2. Then, f takes that output and produces the final result

Think of it as an assembly line. The raw material x enters the first machine (g), which transforms it into an intermediate product g(x). That intermediate product then enters the second machine (f), which transforms it into the final output f(g(x)).

For example, if g(x) = 3x + 1 and f(u) = u², then:

f(g(x)) = f(3x + 1) = (3x + 1)²

The input x first gets tripled and incremented (the g step), then that result gets squared (the f step).

This might seem like a simple concept, but it's the foundation of everything that follows. Neural networks are nothing more than deeply nested function compositions—dozens or hundreds of functions applied in sequence, each transforming the output of the previous one.

## 2. The Pipeline Metaphor

Let's extend our assembly line into a full pipeline visualization. Imagine data flowing through a series of tubes, with each tube containing a transformation:

```
x → [g] → g(x) → [f] → f(g(x))
```

Each box is a function that processes whatever flows into it. The output of one stage becomes the input to the next. This is exactly how a neural network processes data:

```
input → [Layer 1] → [Layer 2] → [Layer 3] → ... → output
```

The key insight is that we can make this pipeline arbitrarily long. Three functions? No problem:

```
x → [h] → h(x) → [g] → g(h(x)) → [f] → f(g(h(x)))
```

Each stage does its own transformation, blissfully unaware of what came before or what comes after. It just transforms its input and passes the result downstream.

## 3. The Problem: Sensitivity Through the Chain

Here's the question that leads us to the chain rule:

**If I wiggle the input x by a tiny amount, how much does the final output wiggle?**

This is asking for the derivative of the composite function. But here's the challenge: the effect of changing x has to propagate through every stage of the pipeline. A small change in x causes a change in g(x), which in turn causes a change in f(g(x)).

It's like a game of telephone, except instead of words getting distorted, we're tracking how much the "signal" gets amplified or dampened at each stage.

Let's think about this concretely. Suppose:
- When x changes by 1, g(x) changes by 2 (so g'(x) = 2)
- When g's output changes by 1, f's output changes by 3 (so f'(g(x)) = 3)

If x increases by a tiny amount Δx:
- g(x) increases by approximately 2·Δx (because g amplifies changes by factor 2)
- f(g(x)) increases by approximately 3·(2·Δx) = 6·Δx (because f amplifies by factor 3)

The overall amplification is 2 × 3 = 6. **The derivatives multiply.**

## 4. Intuitive Chain Rule: Derivatives Multiply Through

This is the core insight of the chain rule, and it's worth burning into your brain:

**When functions are composed, their derivatives multiply.**

Think about why this makes sense. Each function in the chain either amplifies or dampens changes passing through it. If the first function doubles everything (derivative = 2) and the second function triples everything (derivative = 3), then the overall effect is to multiply by 6.

It's like compound interest, or gear ratios. If one gear doubles the rotation speed and the next triples it, the total speedup is 6×.

Here's another way to see it. Suppose you're tracking how a small change propagates:

- Δx causes g(x) to change by g'(x)·Δx
- That change in g(x) causes f(g(x)) to change by f'(g(x))·[g'(x)·Δx]
- Rearranging: the change in f(g(x)) is [f'(g(x))·g'(x)]·Δx

The coefficient in front of Δx is the derivative of the whole composition. It's the product of the individual derivatives.

## 5. The Chain Rule Formula

Now we can state the chain rule precisely:

**d/dx[f(g(x))] = f'(g(x)) · g'(x)**

In words: "The derivative of a composition equals the derivative of the outer function (evaluated at the inner function) times the derivative of the inner function."

Some people remember this as "outer derivative times inner derivative." Others use the mnemonic "derivative of the outside, leave the inside alone, times derivative of the inside."

There's an equivalent notation using Leibniz's dy/dx style that some find more intuitive. If we let u = g(x), then:

**dy/dx = (dy/du) · (du/dx)**

This looks like fraction multiplication where the du's "cancel." They don't actually cancel (these aren't really fractions), but the notation is suggestive and helps many people remember the rule.

The key point in either notation: **multiply the derivatives together**.

## 6. Step-by-Step Example

Let's work through a complete example. Consider:

**h(x) = (3x + 1)²**

We want to find h'(x).

**Step 1: Identify the composition**

This is a composite function. The outer function is "squaring" and the inner function is "3x + 1."

- Outer: f(u) = u²
- Inner: g(x) = 3x + 1

So h(x) = f(g(x)) = (g(x))² = (3x + 1)²

**Step 2: Find the individual derivatives**

- f(u) = u² → f'(u) = 2u
- g(x) = 3x + 1 → g'(x) = 3

**Step 3: Apply the chain rule**

h'(x) = f'(g(x)) · g'(x)

For f'(g(x)), we take f'(u) = 2u and substitute u = g(x) = 3x + 1:
- f'(g(x)) = 2(3x + 1)

So:
h'(x) = 2(3x + 1) · 3 = 6(3x + 1)

**Step 4: Verify (optional)**

We can check this by expanding h(x) first:
- h(x) = (3x + 1)² = 9x² + 6x + 1
- h'(x) = 18x + 6 = 6(3x + 1) ✓

The chain rule gave us the same answer, but with less algebraic grunt work.

## 7. Multiple Links in the Chain

The chain rule extends naturally to longer compositions. For three functions:

**d/dx[f(g(h(x)))] = f'(g(h(x))) · g'(h(x)) · h'(x)**

Just keep multiplying. Each derivative is evaluated at its input—meaning the value that actually flows into that stage of the pipeline:

- f' is evaluated at g(h(x)) — what f actually receives
- g' is evaluated at h(x) — what g actually receives  
- h' is evaluated at x — what h actually receives

For a chain of n functions:

**d/dx[f₁(f₂(f₃(...fₙ(x)...)))] = f₁' · f₂' · f₃' · ... · fₙ'**

where each derivative is evaluated at its respective input.

This is beautiful in its simplicity. No matter how long the chain, you just multiply all the derivatives together. A hundred functions composed? Multiply a hundred derivatives.

## 8. Why This Matters for Machine Learning

The chain rule isn't just another calculus technique—it's the mathematical foundation of how neural networks learn. Here's why.

### Neural Networks Are Function Compositions

A neural network is literally a composition of functions. Each layer applies a transformation:

```
input → [Layer 1] → [Layer 2] → ... → [Layer L] → prediction → [Loss]
```

Layer 1 transforms the input into hidden activations. Layer 2 transforms those activations into new activations. This continues until the final layer produces a prediction. Then a loss function compares that prediction to the true answer.

The entire network, from input to loss, is one giant composite function. If we call the loss L and the input x, then:

L = f_loss(f_L(f_{L-1}(...f_2(f_1(x))...)))

### The Learning Problem

Training a neural network means adjusting the weights to minimize the loss. To do this with gradient descent, we need to know: **how does each weight affect the loss?**

This is a derivative question. Specifically, we need ∂L/∂w for every weight w in the network.

But here's the challenge: any given weight in Layer 1 affects the loss only indirectly. Changing that weight changes Layer 1's output, which changes Layer 2's output, which changes Layer 3's output... eventually affecting the prediction and thus the loss.

The weight's effect on the loss propagates through the entire chain of layers. Sound familiar?

### Backpropagation Is the Chain Rule

Backpropagation—the algorithm that makes deep learning possible—is just the chain rule applied systematically.

During the **forward pass**, data flows from input to output:
```
x → Layer 1 → Layer 2 → ... → Layer L → Loss
```

During the **backward pass**, gradients flow from output to input:
```
∂L/∂x ← Layer 1 ← Layer 2 ← ... ← Layer L ← ∂L/∂Loss = 1
```

At each layer, we multiply by that layer's local derivative. The gradient with respect to early layers is the product of all the derivatives along the path—exactly what the chain rule says.

For a weight w in Layer k, the gradient is:

∂L/∂w = (∂L/∂output_L) · (∂output_L/∂output_{L-1}) · ... · (∂output_{k+1}/∂output_k) · (∂output_k/∂w)

Each term is a local derivative. Multiply them all together, and you get the weight's effect on the loss.

### Why "Backward"?

The algorithm is called backpropagation because we compute derivatives from the end of the network backward to the beginning. This is computationally efficient because we can reuse intermediate results.

If we computed each weight's gradient independently (by tracing forward from that weight to the loss), we'd redo a lot of work. By going backward, we compute ∂L/∂(Layer L output) once, then use that to compute ∂L/∂(Layer L-1 output), and so on. Each layer's gradient builds on the next layer's gradient.

This "backward" flow of gradient information—multiplying derivatives as we go—is the chain rule in action.

## 9. The Computational Graph View

There's a powerful visual way to think about the chain rule: the **computational graph**.

A computational graph represents a computation as a network of nodes and edges:
- **Nodes** are operations (add, multiply, square, apply activation function, etc.)
- **Edges** carry values from one operation to the next

For example, computing (3x + 1)² might look like:

```
x → [×3] → [+1] → [square] → output
```

Each node has:
- **Inputs**: values flowing in
- **Output**: the result of the operation
- **Local gradient**: how the output changes with respect to each input

During the forward pass, values flow left to right. During the backward pass, gradients flow right to left, getting multiplied at each node.

This is exactly how automatic differentiation frameworks like PyTorch and TensorFlow work. When you define a neural network, you're building a computational graph. When you call `.backward()`, the framework traverses the graph in reverse, applying the chain rule at each node to compute all the gradients.

The beauty of this approach is that you never have to derive gradients by hand. The framework knows the local gradient of each operation (multiplication, addition, ReLU, etc.) and combines them using the chain rule automatically.

## 10. A Complete Neural Network Example

Let's trace through a tiny example to make this concrete. Consider a "network" with:
- Input: x
- Single weight: w
- Computation: output = (wx)², and Loss = (output - target)²

The computational graph is:

```
x, w → [multiply: wx] → [square: (wx)²] → [loss: (output - target)²]
```

**Forward pass** (say x = 2, w = 3, target = 10):
- wx = 6
- (wx)² = 36
- Loss = (36 - 10)² = 676

**Backward pass** (computing ∂Loss/∂w):

Start at the loss. ∂Loss/∂Loss = 1.

**At the loss node**: Loss = (output - target)²
- ∂Loss/∂output = 2(output - target) = 2(36 - 10) = 52

**At the square node**: output = (wx)²
- Let u = wx. Then output = u².
- ∂output/∂u = 2u = 2(6) = 12
- By chain rule: ∂Loss/∂u = ∂Loss/∂output · ∂output/∂u = 52 · 12 = 624

**At the multiply node**: u = wx
- ∂u/∂w = x = 2
- By chain rule: ∂Loss/∂w = ∂Loss/∂u · ∂u/∂w = 624 · 2 = 1248

So the gradient of the loss with respect to w is 1248. This tells us: if we increase w slightly, the loss will increase by about 1248 times that amount. To reduce the loss, we should decrease w.

Every step was just multiplication—the chain rule, applied mechanically.

## Wrapping Up

The chain rule is deceptively simple: when functions are composed, their derivatives multiply. But this simple rule is the engine that powers all of deep learning.

When you train a neural network, you're asking: "How does each weight affect the final loss?" The answer requires tracing through every layer of the network, accounting for how changes propagate through each transformation. The chain rule tells you exactly how to do this: multiply the local derivatives together.

Backpropagation is just the chain rule applied efficiently. The "backward" pass flows gradient information from the loss back to each weight, multiplying by local derivatives at every step. This is why neural networks can have millions of parameters and still be trainable—we can compute all those gradients with a single backward pass.

In your visualization, watch how a small change at the input creates a cascade of changes through the pipeline. Each stage amplifies or dampens the effect. The final sensitivity—the derivative of the composition—is the product of all those individual sensitivities.

The chain rule transforms a daunting question ("how does this weight buried in Layer 3 affect my loss?") into a series of simple local questions ("how does each layer affect the next?"), combined by multiplication. That's the magic that makes deep learning work.
