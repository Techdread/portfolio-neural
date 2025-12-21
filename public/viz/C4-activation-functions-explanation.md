# C4: Activation Functions — The Nonlinear Heart of Neural Networks

## Why Activation Functions Matter

Imagine stacking linear transformations. Matrix multiply, then another, then another. What do you get? Just one big linear transformation. No matter how many layers, the whole network collapses to a single matrix multiplication.

```
Layer 1: y = W₁x
Layer 2: z = W₂y = W₂W₁x
Layer 3: out = W₃z = W₃W₂W₁x = Wx  (just one matrix!)
```

This is useless for learning complex patterns. A line can't fit a curve.

Activation functions break this limitation. By inserting a nonlinear function after each layer, we prevent the collapse. Now deep networks can approximate any continuous function—curves, decision boundaries, anything.

```
Layer 1: y = σ(W₁x)      ← nonlinearity!
Layer 2: z = σ(W₂y)      ← nonlinearity!
Layer 3: out = σ(W₃z)    ← cannot simplify
```

The choice of activation function profoundly affects training dynamics, gradient flow, and what the network can learn.

---

## The Classic: Sigmoid

```
σ(x) = 1 / (1 + e⁻ˣ)
```

The sigmoid squashes any input into the range (0, 1). Large positive inputs → near 1. Large negative inputs → near 0. It's smooth, differentiable everywhere, and historically was the default choice.

**The derivative:**
```
σ'(x) = σ(x) · (1 - σ(x))
```

This elegant form means we can compute the derivative from the output alone—no need to store the input.

**The problem:** Look at the derivative formula. When σ(x) is near 0 or 1 (which happens for any |x| > 2), the derivative becomes tiny. Maximum derivative is only 0.25, occurring at x = 0.

**Output range:** (0, 1)

**When to use:** Binary classification output layers, gates in LSTMs/GRUs.

**When to avoid:** Hidden layers in deep networks (vanishing gradient).

---

## Zero-Centered: Tanh

```
tanh(x) = (eˣ - e⁻ˣ) / (eˣ + e⁻ˣ)
```

Tanh is essentially a rescaled sigmoid: tanh(x) = 2σ(2x) - 1. It maps inputs to (-1, 1) instead of (0, 1).

**The derivative:**
```
tanh'(x) = 1 - tanh²(x)
```

**Why zero-centered matters:** Sigmoid outputs are always positive. This means gradients for weights in the next layer are either all positive or all negative, causing inefficient zig-zag updates. Tanh's outputs center around zero, allowing mixed-sign gradients.

**The problem:** Same vanishing gradient issue as sigmoid. For |x| > 2, the derivative approaches zero.

**Output range:** (-1, 1)

**When to use:** Hidden layers when you need bounded, zero-centered outputs. RNNs sometimes prefer tanh.

---

## The Modern Default: ReLU

```
ReLU(x) = max(0, x)
```

Rectified Linear Unit. Elegant simplicity: if positive, pass through; if negative, output zero.

**The derivative:**
```
ReLU'(x) = 1 if x > 0, else 0
```

**Why ReLU revolutionized deep learning:**

1. **No vanishing gradient** for positive inputs. Derivative is exactly 1, no matter how large x gets.
2. **Sparse activation.** Many neurons output zero, making computation efficient.
3. **Fast to compute.** Just a comparison, no exponentials.

**The problem: Dead neurons.** If a neuron's input is always negative (due to unlucky initialization or large learning rates), it outputs zero forever. Zero output means zero gradient. The neuron "dies" and never recovers.

**Output range:** [0, ∞)

**When to use:** Default for hidden layers in most architectures.

---

## Fixing Dead Neurons: Leaky ReLU

```
LeakyReLU(x) = x if x > 0, else αx
```

Where α is a small positive constant, typically 0.01 or 0.1.

**The derivative:**
```
LeakyReLU'(x) = 1 if x > 0, else α
```

Instead of outputting zero for negative inputs, Leaky ReLU outputs a small negative value. This ensures gradients always flow, preventing dead neurons.

**The tradeoff:** Introduces a hyperparameter α. Too small, and you still get near-dead neurons. Too large, and you lose the benefits of sparsity.

**Variants:**
- **PReLU (Parametric ReLU):** α is learned during training
- **RReLU (Randomized ReLU):** α is sampled randomly during training

**Output range:** (-∞, ∞)

---

## Smooth Negative Region: ELU

```
ELU(x) = x if x > 0, else α(eˣ - 1)
```

Exponential Linear Unit. For positive inputs, it's linear like ReLU. For negative inputs, it smoothly saturates to -α.

**The derivative:**
```
ELU'(x) = 1 if x > 0, else α·eˣ = ELU(x) + α
```

**Advantages over ReLU:**
1. **Zero-centered outputs** (mean closer to zero than ReLU)
2. **Smooth everywhere** (no kink at x = 0)
3. **Noise-robust** (saturates for very negative inputs)

**The tradeoff:** Requires computing exponentials, slower than ReLU.

**Output range:** (-α, ∞)

---

## State of the Art: GELU

```
GELU(x) = x · Φ(x)
```

Where Φ(x) is the cumulative distribution function of the standard normal distribution.

**Practical approximation:**
```
GELU(x) ≈ 0.5x(1 + tanh(√(2/π)(x + 0.044715x³)))
```

GELU stands for Gaussian Error Linear Unit. It's the default activation in transformers (BERT, GPT, etc.).

**Intuition:** GELU can be thought of as a smooth version of ReLU where the "gate" (whether to pass the input) is probabilistic based on the input's magnitude. Larger positive inputs are more likely to pass through unchanged.

**The derivative (exact form is complex):**
```
GELU'(x) ≈ 0.5(1 + tanh(...)) + 0.5x · sech²(...) · (...)
```

**Why GELU works well:**
1. **Smooth** — no kink, better gradient flow
2. **Non-monotonic** — has a small dip around x ≈ -0.5
3. **Approximates expectations** — relates to stochastic regularization

**Output range:** approximately (-0.17, ∞)

**When to use:** Transformers, modern architectures, whenever you want smooth ReLU.

---

## Self-Gated: Swish

```
Swish(x) = x · σ(x)
```

Discovered through neural architecture search by Google. Swish is simply the input multiplied by its sigmoid.

**The derivative:**
```
Swish'(x) = σ(x) + x · σ(x) · (1 - σ(x))
           = Swish(x) + σ(x)(1 - Swish(x))
```

**Properties:**
- Smooth and non-monotonic (like GELU)
- Self-gated: the sigmoid acts as a learned gate
- Bounded below (≈ -0.28) but unbounded above

**Relationship to GELU:** Swish and GELU are remarkably similar in shape. GELU tends to perform slightly better in transformers, while Swish sometimes wins in CNNs.

**Output range:** approximately (-0.28, ∞)

---

## Smooth ReLU: Softplus

```
Softplus(x) = (1/β) · ln(1 + e^(βx))
```

Where β controls sharpness (default β = 1).

**The derivative:**
```
Softplus'(x) = 1 / (1 + e^(-βx)) = σ(βx)
```

The derivative of softplus is sigmoid! This creates a beautiful connection between the two functions.

**Properties:**
- Smooth approximation of ReLU
- As β → ∞, approaches ReLU
- Always positive (never exactly zero)

**The tradeoff:** Never truly sparse. Outputs are always slightly positive, even for large negative inputs.

**Output range:** (0, ∞)

**When to use:** When you need ReLU-like behavior but require smoothness (e.g., for certain optimization algorithms).

---

## The Vanishing Gradient Problem

Here's why activation function choice matters so much for deep networks.

During backpropagation, gradients multiply through layers:

```
∂Loss/∂w₁ = ∂Loss/∂out · ∂out/∂h₃ · ∂h₃/∂h₂ · ∂h₂/∂h₁ · ∂h₁/∂w₁
```

Each `∂hᵢ/∂hᵢ₋₁` includes the activation function's derivative. If that derivative is less than 1, gradients shrink exponentially:

**Sigmoid example:**
- Maximum derivative: 0.25
- After 10 layers: 0.25¹⁰ ≈ 0.000001
- After 20 layers: effectively zero

The gradient has "vanished." Early layers receive no learning signal. Training stalls.

**ReLU comparison:**
- Derivative for positive inputs: 1
- After 10 layers: 1¹⁰ = 1
- After 50 layers: still 1

Gradients flow unchanged. Deep networks can actually learn.

This is why ReLU and its variants dominate modern architectures. They solve the fundamental problem that made deep networks impossible to train.

---

## Exploding Gradients

The opposite problem exists too. If derivatives are greater than 1, gradients grow exponentially:

```
Derivative = 1.1
After 50 layers: 1.1⁵⁰ ≈ 117
After 100 layers: 1.1¹⁰⁰ ≈ 13,780
```

Weights update by enormous amounts, causing numerical instability and NaN losses.

**Solutions:**
1. **Gradient clipping:** Cap gradient magnitudes
2. **Careful initialization:** Match variance across layers
3. **Normalization layers:** BatchNorm, LayerNorm stabilize activations
4. **Residual connections:** Skip connections provide gradient highways

---

## Choosing an Activation Function

**For hidden layers in most networks:**
→ Start with ReLU. It's fast, effective, and well-understood.

**If you see dead neurons (many zeros):**
→ Try Leaky ReLU or ELU.

**For transformers and attention models:**
→ Use GELU. It's the standard for good reason.

**For output layers:**
- Binary classification → Sigmoid (gives probability)
- Multi-class classification → Softmax (gives distribution)
- Regression → Linear (no activation) or ReLU for positive outputs

**For RNNs/LSTMs:**
→ Tanh for cell states, sigmoid for gates (built into the architecture)

---

## Comparing Derivatives

The derivative at a point tells you how much gradient will flow through that neuron.

| Function | Max Derivative | At x = 0 | At x = 3 |
|----------|---------------|----------|----------|
| Sigmoid | 0.25 | 0.25 | 0.045 |
| Tanh | 1.0 | 1.0 | 0.01 |
| ReLU | 1.0 | undefined | 1.0 |
| Leaky ReLU (α=0.1) | 1.0 | 0.1 or 1.0 | 1.0 |
| GELU | ~1.08 | 0.5 | ~1.0 |

Notice how sigmoid and tanh derivatives collapse for large inputs, while ReLU and GELU maintain healthy gradients.

---

## Key Takeaways

1. **Activation functions add nonlinearity**, enabling networks to learn complex patterns.

2. **Sigmoid and tanh suffer from vanishing gradients** in deep networks.

3. **ReLU revolutionized deep learning** by maintaining gradient flow, but can cause dead neurons.

4. **Leaky ReLU and ELU fix the dead neuron problem** by allowing small negative outputs.

5. **GELU is the modern default for transformers**, combining smoothness with ReLU-like behavior.

6. **The derivative matters more than the function itself** for training dynamics.

7. **Deep networks require activation functions with derivatives near 1** for stable training.

Understanding these functions isn't just academic—it directly affects whether your network trains successfully and how deep you can go.
