# C3: Computational Graphs — The Structure Behind Autodiff

## Expressions as Trees

Every mathematical expression has a hidden structure. Consider this simple function:

```
f(x, y) = x² + xy
```

You might read this left-to-right as text, but a computer sees it as a tree:

```
        [+]
       /   \
    [×]     [×]
   /   \   /   \
  x     x x     y
```

The top node (+) depends on two multiplication results. Each multiplication depends on its inputs. The leaves—x and y—are where actual values enter.

This isn't just a visualization trick. It's how computers *actually* evaluate expressions. And more importantly, it's how they compute derivatives automatically.

---

## Nodes and Edges

A computational graph has three types of components:

**Leaf Nodes**: The starting points. These are:
- Input variables (x, y, z)
- Constants (2, π, 0.5)
- Learned parameters (weights, biases)

Leaf nodes have values but no dependencies. They're where computation begins.

**Internal Nodes**: Operations that transform data. Common ones include:
- Arithmetic: +, −, ×, ÷
- Powers: x², √x, xⁿ
- Functions: sin, cos, exp, log
- Comparisons: max, min, ReLU

Each internal node takes inputs and produces one output.

**Edges**: Data flow connections. An edge from A to B means "B uses A's output as input." Edges point from dependencies toward dependents—from leaves toward the root.

Here's our expression with node types labeled:

```
            [+] ← Internal (addition)
           /   \
   Internal → [×]     [×] ← Internal (multiply)
         /   \   /   \
 Leaf → x     x x     y ← Leaf
```

---

## Forward Mode: Evaluation

Forward evaluation flows from leaves to root. You start with input values and compute upward until you reach the final result.

Let's evaluate f(x, y) = x² + xy with x = 3, y = 4:

**Step 1**: Assign values to leaves
```
x = 3
y = 4
```

**Step 2**: Evaluate left subtree (x²)
```
x × x = 3 × 3 = 9
```

**Step 3**: Evaluate right subtree (xy)
```
x × y = 3 × 4 = 12
```

**Step 4**: Evaluate root (sum)
```
9 + 12 = 21
```

The graph with computed values:

```
           [+] = 21
          /    \
    [×] = 9    [×] = 12
      /  \      /  \
   x=3  x=3  x=3  y=4
```

This is the **forward pass**. Every value flows upward. The root holds the final answer.

---

## The Gradient Problem

Forward evaluation is straightforward. But here's the challenge that makes machine learning possible:

**Given f(x, y) = x² + xy, what are ∂f/∂x and ∂f/∂y?**

You could compute these symbolically:
- ∂f/∂x = 2x + y
- ∂f/∂y = x

But symbolic differentiation has problems. For complex functions with thousands of operations, symbolic expressions explode in size. And what about control flow—if statements, loops?

We need a better approach: **compute derivatives numerically, but exactly, by following the graph structure.**

---

## Backward Mode (Reverse Mode Autodiff)

Here's the key insight: if we recorded how we computed the output, we can trace backward to find how each input affected it.

**The Algorithm**:

1. Start at the root. Set its gradient to 1 (∂f/∂f = 1).
2. For each node, compute gradients for its inputs using local rules.
3. Propagate backward until you reach the leaves.
4. Leaf gradients are your answers: ∂f/∂x, ∂f/∂y, etc.

Let's trace through f(x, y) = x² + xy at x = 3, y = 4.

First, the forward pass (which we already computed):

```
           [+] = 21
          /    \
    [×] = 9    [×] = 12
      /  \      /  \
   x=3  x=3  x=3  y=4
```

Now, backward pass:

**Step 1**: Root gradient
```
∂f/∂(root) = 1
```
The output's gradient with respect to itself is always 1.

**Step 2**: Propagate through addition
Addition passes gradients unchanged to both inputs:
```
∂f/∂(left ×) = 1
∂f/∂(right ×) = 1
```

**Step 3**: Propagate through left multiplication (x × x)
For multiplication y = a × b:
- ∂y/∂a = b
- ∂y/∂b = a

The left multiplication computes x × x. Both inputs are x, so:
- Gradient to left input: 1 × x = 1 × 3 = 3
- Gradient to right input: 1 × x = 1 × 3 = 3

**Step 4**: Propagate through right multiplication (x × y)
- Gradient to x input: 1 × y = 1 × 4 = 4
- Gradient to y input: 1 × x = 1 × 3 = 3

**Step 5**: Accumulate at leaves
Variable x appears three times as a leaf. Gradients accumulate:
```
∂f/∂x = 3 + 3 + 4 = 10
```

Variable y appears once:
```
∂f/∂y = 3
```

**Verification**: Using our symbolic derivatives:
- ∂f/∂x = 2x + y = 2(3) + 4 = 10 ✓
- ∂f/∂y = x = 3 ✓

The graph traced it perfectly.

---

## Local Gradient Rules

Each operation type has a simple backward rule. The node receives a gradient from above (call it `grad`) and computes gradients for its inputs.

### Addition: y = a + b

```
Forward:  y = a + b
Backward: ∂L/∂a = grad × 1 = grad
          ∂L/∂b = grad × 1 = grad
```

Addition distributes the gradient equally. If the output matters by amount `grad`, each input matters by the same amount.

### Subtraction: y = a − b

```
Forward:  y = a - b
Backward: ∂L/∂a = grad × 1 = grad
          ∂L/∂b = grad × (-1) = -grad
```

The first input receives the gradient unchanged; the second receives it negated.

### Multiplication: y = a × b

```
Forward:  y = a × b
Backward: ∂L/∂a = grad × b
          ∂L/∂b = grad × a
```

Each input's gradient is the incoming gradient times the *other* input's value. This is why we store values during the forward pass—we need them for backward.

### Division: y = a / b

```
Forward:  y = a / b
Backward: ∂L/∂a = grad × (1/b)
          ∂L/∂b = grad × (-a/b²)
```

Division is trickier—the denominator's gradient involves the quotient rule.

### Power: y = xⁿ

```
Forward:  y = xⁿ
Backward: ∂L/∂x = grad × n × x^(n-1)
```

The power rule, multiplied by the incoming gradient.

### Common Functions

**Sine**: y = sin(x)
```
Backward: ∂L/∂x = grad × cos(x)
```

**Cosine**: y = cos(x)
```
Backward: ∂L/∂x = grad × (-sin(x))
```

**Exponential**: y = eˣ
```
Backward: ∂L/∂x = grad × eˣ = grad × y
```

**Logarithm**: y = log(x)
```
Backward: ∂L/∂x = grad × (1/x)
```

**ReLU**: y = max(0, x)
```
Backward: ∂L/∂x = grad × (1 if x > 0 else 0)
```

Each operation only needs to know its own rule. The chain rule handles composition automatically through gradient propagation.

---

## A More Complex Example

Let's trace a function closer to what neural networks use:

```
f(x, w) = sigmoid(w × x)
```

With x = 2, w = 0.5:

**Forward Pass**:
```
        [σ] = 0.7311
         |
        [×] = 1.0
       /   \
    w=0.5  x=2
```

Step by step:
1. Multiply: 0.5 × 2 = 1.0
2. Sigmoid: 1/(1 + e^(-1)) = 0.7311

**Backward Pass**:

Start with ∂f/∂f = 1.

**Through sigmoid**:
```
∂f/∂(×) = 1 × σ(1) × (1 - σ(1))
        = 1 × 0.7311 × 0.2689
        = 0.1966
```

**Through multiplication**:
```
∂f/∂w = 0.1966 × x = 0.1966 × 2 = 0.3932
∂f/∂x = 0.1966 × w = 0.1966 × 0.5 = 0.0983
```

We now know exactly how sensitive the output is to each input. Changing w by a small amount δ changes the output by approximately 0.3932 × δ.

---

## Why Graphs Enable Autodiff

The computational graph representation makes automatic differentiation possible for three reasons:

**1. Every Operation is Recorded**

When you write `z = x * y` in PyTorch or TensorFlow, you're not just computing a number—you're adding a node to a graph. The framework remembers what operation you performed and what the inputs were.

```python
x = torch.tensor(3.0, requires_grad=True)
y = torch.tensor(4.0, requires_grad=True)
z = x * y  # Graph now has: z = multiply(x, y)
```

**2. Backward Follows the Recorded Path**

When you call `.backward()`, the framework walks the graph in reverse. It doesn't need to know what function you wrote—it just needs to traverse the nodes and apply local rules.

```python
z.backward()  # Traverse graph, apply rules
print(x.grad)  # 4.0 (which is y)
print(y.grad)  # 3.0 (which is x)
```

**3. Composition Happens Automatically**

The chain rule multiplication happens through propagation. No node needs to understand the global function. Each just passes gradients according to its local rule. The graph structure encodes how they combine.

---

## Dynamic vs Static Graphs

Modern frameworks differ in *when* they build the graph:

### Static Graphs (Old TensorFlow 1.x)

Define the entire computation first, then run it:

```python
# Define graph
x = tf.placeholder(...)
y = tf.matmul(W, x)
z = tf.nn.relu(y)

# Then execute
session.run(z, feed_dict={x: data})
```

**Pros**: Optimization opportunities, deployment efficiency
**Cons**: Hard to debug, no Python control flow

### Dynamic Graphs (PyTorch, TensorFlow 2.x)

Build the graph as you execute:

```python
x = torch.tensor(data)
y = W @ x          # Graph builds here
z = torch.relu(y)  # And here
z.backward()       # Traverse what we built
```

**Pros**: Natural Python, easy debugging, flexible control flow
**Cons**: Some optimization opportunities lost

Dynamic graphs won. The ability to use normal Python `if` statements, loops, and debugging tools outweighed the performance cost. PyTorch's approach became the standard, and TensorFlow 2.x adopted it.

---

## Why This Matters for ML/AI

Understanding computational graphs unlocks several insights:

### Neural Networks ARE Computational Graphs

A neural network is just a large computational graph. Inputs flow forward through operations (matrix multiplies, activations, normalizations). Loss computation adds more nodes. Backpropagation traverses this graph in reverse.

When you call `model(x)`, you're building a graph. When you call `loss.backward()`, you're running reverse-mode autodiff on that graph.

### Autodiff = Automatic Backprop

You never write backpropagation code. The framework does it for you. Every operation you use (conv2d, batch_norm, attention) comes with backward rules. Compose them however you want—gradients flow correctly.

This is why you can invent new architectures freely. As long as you use differentiable operations, gradients happen automatically.

### Debugging Gradient Issues

When gradients explode, vanish, or become NaN, understanding the graph helps:

- **Vanishing gradients**: Long chains of small multiplications (like repeated sigmoid)
- **Exploding gradients**: Long chains of large multiplications
- **NaN gradients**: Division by zero, log of negative numbers, or invalid operations somewhere in the graph

Visualizing the graph often reveals where problems originate. Many tools (TensorBoard, PyTorch's `torchviz`) can render your graph for inspection.

---

## Visualizing the Flow

In the interactive visualization, watch for:

1. **Forward pass**: Values propagate from leaves (inputs) upward to the root (output)
2. **Backward initialization**: Root receives gradient = 1
3. **Gradient propagation**: Each node applies its local rule and passes gradients down
4. **Accumulation at leaves**: Variables used multiple times collect gradients from all paths

The tree structure makes the flow explicit. Every gradient has a path it followed. Every derivative has a chain of multiplications that produced it.

---

## Key Takeaways

1. **Expressions are trees** with leaves (inputs) and internal nodes (operations)
2. **Forward mode** evaluates from leaves to root, computing values
3. **Backward mode** starts at the root with gradient 1, propagates using local rules
4. **Each operation has a simple backward rule**—addition passes through, multiplication swaps inputs, power uses the power rule
5. **Gradients accumulate** when a variable appears multiple times
6. **Frameworks build graphs automatically** as you compute
7. **This is why autodiff works**: the graph encodes exactly how to reverse the computation

With computational graphs, you don't compute gradients—you let the structure compute them for you.
