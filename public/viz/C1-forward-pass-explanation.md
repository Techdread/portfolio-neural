# The Neural Network Forward Pass — Step by Step

You've learned how vectors carry data and how matrix multiplication transforms that data. Now we'll see these tools in action inside a neural network. A forward pass is simply data flowing through the network, being transformed at each step until a result emerges at the end.

---

## What is a Forward Pass?

Imagine a factory assembly line. Raw materials enter one end, pass through several workstations where they're shaped and modified, and a finished product comes out the other end. A neural network works the same way.

**The forward pass is the journey data takes from input to output.**

When you give a neural network an image and it tells you "cat," that answer came from a forward pass. When a language model predicts the next word, that prediction came from a forward pass. Every time a neural network produces an output, it has performed a forward pass.

Here's the key insight: **a forward pass is just arithmetic**. Multiplication, addition, and simple functions—repeated many times. Nothing more mysterious than that.

The data flows in one direction:

```
Input → Layer 1 → Layer 2 → ... → Layer N → Output
```

At each layer, three things happen:
1. Multiply inputs by weights
2. Add a bias
3. Apply an activation function

Let's break down exactly what this means.

---

## The Single Neuron

A neuron is the basic computing unit of a neural network. Despite the biological name, it's just a small mathematical function. Here's what a single neuron does:

### Step 1: Receive Multiple Inputs

A neuron receives several numbers as input. These might be:
- Pixel values from an image
- Features from previous neurons
- Any numerical data you're processing

Let's say our neuron receives three inputs: **x₁ = 2**, **x₂ = 3**, **x₃ = 1**

### Step 2: Multiply Each Input by a Weight

Every input has an associated **weight**—a number that determines how much that input matters. The neuron has learned these weights during training.

Let's say our weights are: **w₁ = 0.5**, **w₂ = -0.3**, **w₃ = 0.8**

We multiply each input by its weight:
- w₁ × x₁ = 0.5 × 2 = **1.0**
- w₂ × x₂ = -0.3 × 3 = **-0.9**
- w₃ × x₃ = 0.8 × 1 = **0.8**

### Step 3: Sum All Weighted Inputs

Add up all those products:

**1.0 + (-0.9) + 0.8 = 0.9**

This is the **weighted sum**. If you remember dot products from our vectors lesson, you'll recognize this: we just computed the dot product of the input vector [2, 3, 1] and the weight vector [0.5, -0.3, 0.8].

### Step 4: Add a Bias

The **bias** is a single number added to the weighted sum. Think of it as the neuron's "baseline" or "offset."

Let's say our bias is: **b = 0.1**

**0.9 + 0.1 = 1.0**

### Step 5: Apply an Activation Function

Finally, we pass this result through an **activation function**. For now, let's use ReLU (Rectified Linear Unit), which is the simplest: if the number is negative, output 0; if positive, output the number unchanged.

Our value is 1.0 (positive), so:

**ReLU(1.0) = 1.0**

This is our neuron's output: **1.0**

### The Complete Formula

We can write everything a neuron does in one formula:

```
output = activation(w₁x₁ + w₂x₂ + w₃x₃ + b)
```

Or more generally:

```
output = activation(Σ wᵢxᵢ + b)
```

That sigma (Σ) just means "sum up all the weighted inputs." The entire neuron computation fits in this one line.

---

## Why Weights and Biases?

### Weights: The Importance Dial

Each weight controls how much its corresponding input influences the output.

- **Large positive weight** (like 2.0): "This input is very important—when it goes up, push my output up strongly"
- **Small positive weight** (like 0.1): "This input matters a little"
- **Negative weight** (like -0.5): "This input matters, but inversely—when it goes up, push my output down"
- **Zero weight**: "Ignore this input completely"

During training, the network learns which inputs matter for which decisions. A neuron detecting edges in images might learn high weights for adjacent pixels with contrasting values.

### Bias: Shifting the Threshold

The bias shifts when the neuron "activates."

Without any bias, a neuron with all positive weights would need at least some positive input to produce output. The bias can change this:

- **Positive bias** (+2): The neuron is "eager"—it produces output even with weak or zero inputs
- **Negative bias** (-2): The neuron is "reluctant"—inputs need to be stronger to overcome this deficit

Think of bias as moving the decision boundary. If a neuron decides "cat vs. not cat," the bias shifts where that boundary sits.

---

## Activation Functions: Adding Non-Linearity

Here's a crucial question: why bother with activation functions? Why not just output the weighted sum directly?

Without activation functions, stacking layers would be pointless. Two linear transformations in a row can always be collapsed into a single linear transformation. No matter how many layers you stack, the network could only learn linear relationships.

Activation functions add **non-linearity**—the ability to learn curves, boundaries, and complex patterns.

Common activation functions:

| Function | Formula | When output is... |
|----------|---------|-------------------|
| **ReLU** | max(0, x) | 0 if negative, x if positive |
| **Sigmoid** | 1/(1 + e⁻ˣ) | Always between 0 and 1 |
| **Tanh** | (eˣ - e⁻ˣ)/(eˣ + e⁻ˣ) | Always between -1 and 1 |

ReLU is most popular for hidden layers because it's simple and trains well. We'll explore these in detail in a later lesson (C4). For now, just know: **activation functions are what give neural networks their power to learn complex patterns**.

---

## From Neuron to Layer

A single neuron is limited—it can only output one number. Real neural networks have layers containing many neurons working in parallel.

### A Layer = Many Neurons, Same Inputs

Imagine four neurons, each receiving the same three inputs. Each neuron has its own weights and bias, so each produces a different output.

Here's the insight that connects to your matrix multiplication knowledge:

**One neuron**: dot product of inputs with weights, add bias
**Many neurons**: matrix multiplication of inputs with weight matrix, add bias vector

If we have:
- Input vector: **x** = [x₁, x₂, x₃]
- Weight matrix: **W** (each row is one neuron's weights)
- Bias vector: **b** = [b₁, b₂, b₃, b₄]

Then all neurons compute at once:

```
output = activation(W · x + b)
```

This is exactly the matrix multiplication you learned! The weight matrix transforms the input vector into a new vector, we add the bias vector, and apply activation to each element.

### Concrete Example: 3 Inputs → 2 Neurons

Input: **x** = [2, 3, 1]

Weight matrix (2 neurons, each with 3 weights):
```
W = | 0.5  -0.3   0.8 |  ← neuron 1's weights
    | 0.2   0.4  -0.1 |  ← neuron 2's weights
```

Bias vector: **b** = [0.1, -0.2]

**Step 1: Matrix multiplication**
```
W · x = | 0.5×2 + (-0.3)×3 + 0.8×1 |   =   | 1.0 - 0.9 + 0.8 |   =   | 0.9 |
        | 0.2×2 + 0.4×3 + (-0.1)×1 |       | 0.4 + 1.2 - 0.1 |       | 1.5 |
```

**Step 2: Add bias**
```
| 0.9 |   +   | 0.1  |   =   | 1.0 |
| 1.5 |       | -0.2 |       | 1.3 |
```

**Step 3: Apply ReLU to each element**
```
ReLU(| 1.0 |) = | 1.0 |
     | 1.3 |    | 1.3 |
```

Layer output: **[1.0, 1.3]**

Both values were positive, so ReLU passed them through unchanged. If either had been negative, it would become 0.

---

## Multiple Layers: Composing Transformations

The real power comes from stacking layers. The output of layer 1 becomes the input to layer 2.

```
Input → [Layer 1] → [Layer 2] → [Layer 3] → Output
   x        h₁          h₂          y
```

Mathematically, this is **function composition**. If each layer is a function:

```
y = f₃(f₂(f₁(x)))
```

Each layer transforms the data into a new "representation." Early layers might detect simple patterns (edges, basic shapes). Later layers combine those into complex concepts (faces, objects, meanings).

The forward pass computes this chain, layer by layer, feeding each output into the next input.

---

## Complete Worked Example with Numbers

Let's trace every single number through a complete network:

**Network Architecture**:
- 2 input neurons
- 2 hidden neurons (one hidden layer)
- 1 output neuron

**The Data**:
- Input: **x** = [0.5, 0.8]

**Layer 1 (Hidden Layer) Parameters**:
```
W₁ = | 0.4   0.3 |      b₁ = | 0.1  |
     | -0.2  0.5 |           | -0.1 |
```

**Layer 2 (Output Layer) Parameters**:
```
W₂ = | 0.6  -0.4 |      b₂ = | 0.2 |
```

### Forward Pass: Layer 1

**Step 1.1: Matrix Multiplication**

For hidden neuron 1:
```
0.4 × 0.5 + 0.3 × 0.8 = 0.2 + 0.24 = 0.44
```

For hidden neuron 2:
```
-0.2 × 0.5 + 0.5 × 0.8 = -0.1 + 0.4 = 0.30
```

Result: **[0.44, 0.30]**

**Step 1.2: Add Bias**
```
| 0.44 |   +   | 0.1  |   =   | 0.54 |
| 0.30 |       | -0.1 |       | 0.20 |
```

Result: **[0.54, 0.20]**

**Step 1.3: Apply ReLU**
```
ReLU(0.54) = 0.54  (positive, unchanged)
ReLU(0.20) = 0.20  (positive, unchanged)
```

**Hidden layer output: h = [0.54, 0.20]**

### Forward Pass: Layer 2

Now **h = [0.54, 0.20]** becomes our input.

**Step 2.1: Matrix Multiplication**
```
0.6 × 0.54 + (-0.4) × 0.20 = 0.324 - 0.08 = 0.244
```

Result: **[0.244]**

**Step 2.2: Add Bias**
```
0.244 + 0.2 = 0.444
```

Result: **[0.444]**

**Step 2.3: Apply Activation**

For the output layer, we might use sigmoid (especially for classification):
```
sigmoid(0.444) = 1 / (1 + e^(-0.444))
               = 1 / (1 + 0.641)
               = 1 / 1.641
               = 0.609
```

**Final Output: 0.609**

### Summary Table

| Stage | Computation | Result |
|-------|-------------|--------|
| Input | — | [0.5, 0.8] |
| L1: W₁·x | Matrix multiply | [0.44, 0.30] |
| L1: + b₁ | Add bias | [0.54, 0.20] |
| L1: ReLU | Activation | [0.54, 0.20] |
| L2: W₂·h | Matrix multiply | [0.244] |
| L2: + b₂ | Add bias | [0.444] |
| L2: sigmoid | Activation | **[0.609]** |

That's it. The entire forward pass was just multiplication, addition, and two simple functions (ReLU and sigmoid). No magic—just arithmetic repeated in a specific structure.

---

## Why This Matters for ML/AI

Understanding the forward pass unlocks everything else in deep learning:

### 1. Prediction = One Forward Pass

When you use a trained model, you're running forward passes. Every ChatGPT response, every image classification, every recommendation—it's forward passes producing outputs.

### 2. Inference Time = Sum of Layer Computations

The time to get a prediction depends on:
- Number of layers (depth)
- Size of each layer (width)
- Complexity of operations

Bigger matrices = more multiplications = slower inference. This is why model optimization matters.

### 3. Forward Pass is Prerequisite for Backpropagation

Training a neural network requires **backpropagation**—computing how to adjust weights to reduce errors. But backprop needs the forward pass first:

1. Forward pass: compute output
2. Calculate error: compare output to correct answer
3. Backward pass: trace error back through layers to compute weight updates

You can't train without understanding forward passes. And in the backward pass, you'll retrace every operation we covered, computing gradients along the way.

### 4. Debugging and Intuition

When a model behaves unexpectedly, understanding the forward pass helps you diagnose issues:
- Are activations dying (all zeros after ReLU)?
- Are values exploding (growing huge through layers)?
- Is data shaped correctly at each layer?

---

## Key Takeaways

1. **A forward pass is data flowing through layers** from input to output
2. **Each neuron computes**: weighted sum + bias + activation
3. **Weights determine importance** of each input; biases shift thresholds
4. **Activation functions add non-linearity**—without them, stacking layers is pointless
5. **Matrix multiplication handles entire layers** at once—it's not just convenient, it's computationally efficient
6. **Stacking layers = composing functions**, building complex transformations from simple ones
7. **The entire process is just arithmetic**: multiply, add, apply simple functions, repeat

In your visualization, you'll see these numbers flowing through the network. Watch how different weights create different transformations. Notice how negative weighted sums become zero after ReLU. See the data reshape itself at each layer until a final answer emerges.

The forward pass is where neural networks turn inputs into outputs. Next, we'll learn how networks learn those weights and biases in the first place—through backpropagation.

---

*Next: C2 — Understanding Loss Functions: How Networks Know They're Wrong*
