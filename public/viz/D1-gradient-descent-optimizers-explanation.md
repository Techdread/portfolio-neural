# Gradient Descent Optimizers: From Vanilla to Adam

## The Journey Down the Mountain

Imagine you're blindfolded on a mountainside, trying to reach the lowest valley. You can only feel the slope directly beneath your feet. Gradient descent is exactly this — taking steps downhill based on local information, hoping to find the bottom.

But *how* you take those steps matters enormously. Step too cautiously and you'll take forever. Step too aggressively and you'll overshoot and oscillate. Step without memory and you'll get stuck in every small dip along the way.

This is why we have different optimizers. Each represents a different strategy for navigating that mountain — and watching them race across the same terrain reveals their personalities beautifully.

---

## 1. Vanilla Gradient Descent: The Cautious Walker

### The Simple Idea

Vanilla gradient descent is the most straightforward approach: measure the slope, step downhill. Repeat.

The update rule is elegant:

```
θ = θ - α∇L
```

In plain English: *new position = old position - (learning rate × gradient)*

The gradient ∇L tells you which direction is uphill. The negative sign flips it to point downhill. The learning rate α controls your step size.

### Where It Struggles

Watch vanilla SGD on the "Ravine" surface in the visualization. You'll see it doing something frustrating: **oscillating back and forth** across the narrow valley while making slow progress along the valley floor.

Why? The gradient points toward the nearest downhill direction, which is often *across* the ravine rather than *along* it. Each step overshoots, then the next step overshoots back the other way.

**Three core problems:**

1. **Ravines cause oscillation**: When the loss surface is steep in one direction and shallow in another, the optimizer bounces between the steep walls instead of rolling down the gentle slope.

2. **Local minima are traps**: With no memory of past movement, vanilla SGD stops the moment it finds any flat spot — even a tiny dip that isn't the true minimum.

3. **Learning rate is critical**: Too high and you diverge. Too low and training takes forever. The "right" value depends on the landscape, which you don't know in advance.

Despite these limitations, vanilla SGD remains important to understand — it's the foundation everything else builds upon.

---

## 2. Momentum: The Rolling Ball

### The Intuition

Imagine replacing our cautious walker with a ball rolling downhill. A ball doesn't just respond to the current slope — it has **velocity**. It accumulates speed when rolling in a consistent direction and resists sudden changes.

This is momentum. Instead of stepping based only on the current gradient, we maintain a velocity that builds up over time.

### The Update Rule

```
v = βv + ∇L
θ = θ - αv
```

Two steps now:
1. Update velocity: *new velocity = (friction × old velocity) + current gradient*
2. Update position: *move by velocity scaled by learning rate*

The β (beta) parameter is typically 0.9, meaning we keep 90% of our previous velocity. This is sometimes called the "momentum coefficient" or "friction" (though it acts like anti-friction — higher values mean more momentum is preserved).

### Why This Helps

**Dampens oscillations**: In that ravine, the side-to-side oscillations cancel out over time — one step pushes left, the next pushes right, but these average toward zero. Meanwhile, the consistent downhill gradient *along* the ravine accumulates. The ball gains speed in the right direction while the sideways bouncing diminishes.

**Escapes shallow local minima**: Watch what happens on the "Local Minima Field" surface. Vanilla SGD gets trapped in the first dip it encounters. But momentum carries the ball through small bumps — it has enough speed to roll up and over minor obstacles.

**Accelerates in consistent directions**: When gradients consistently point the same way, velocity builds up, effectively increasing the learning rate in that direction. This is exactly what you want for faster convergence.

### The Ball Analogy in Practice

Think of β as controlling how "heavy" the ball is:
- **β = 0**: No momentum at all (vanilla SGD)
- **β = 0.9**: A bowling ball — hard to stop, smoothly rolls through small obstacles
- **β = 0.99**: A boulder — enormous momentum, but can overshoot badly

The sweet spot for most problems is around 0.9.

---

## 3. RMSprop: The Adaptive Walker

### A Different Problem

Momentum addresses *temporal* issues — how we move over time. But there's another problem: **different parameters need different learning rates**.

Consider a neural network learning to recognise images. Some weights might connect to frequently-activated features (like edges, which appear everywhere). Others might connect to rare features (like a specific texture that appears in few training examples).

The frequent-feature weights get large, consistent gradients. The rare-feature weights get small, sporadic gradients. If we use the same learning rate for both:
- Too high: the frequent-feature weights explode
- Too low: the rare-feature weights barely move

We need learning rates that **adapt per parameter**.

### The RMSprop Solution

RMSprop tracks how large gradients have been for each parameter, then divides by this to normalise:

```
S = ρS + (1-ρ)g²
θ = θ - α × g / √(S + ε)
```

Breaking this down:
1. **S** is a running average of squared gradients (element-wise)
2. **ρ** (rho, typically 0.9) controls how much history to keep
3. We divide the gradient by √S before stepping
4. **ε** (epsilon, ~10⁻⁸) prevents division by zero

### The Effect

Parameters with consistently large gradients accumulate large S values. Dividing by √S shrinks their effective learning rate.

Parameters with small or sparse gradients have small S values. Dividing by √S boosts their effective learning rate.

The result: all parameters make roughly similar *proportional* progress, regardless of their gradient magnitudes.

### Why "Root Mean Square"?

The name describes the math: we're tracking the **mean** of **squared** gradients, then taking the **root** when we use it. This gives us a measure of gradient magnitude that's always positive and doesn't cancel out oscillations.

RMSprop was proposed by Geoffrey Hinton in a Coursera lecture — never formally published — yet became enormously influential. It works particularly well on problems where the loss landscape changes during training (non-stationary problems), like recurrent neural networks.

---

## 4. Adam: The Best of Both Worlds

### Combining the Ideas

Adam (Adaptive Moment Estimation) asks: why choose between momentum and adaptive learning rates? Let's have both.

Adam maintains two running averages:
- **First moment (m)**: The mean of gradients — this is momentum
- **Second moment (v)**: The mean of squared gradients — this is RMSprop

```
m = β₁m + (1-β₁)g          # Momentum-style accumulation
v = β₂v + (1-β₂)g²         # RMSprop-style accumulation

m̂ = m / (1-β₁ᵗ)            # Bias correction
v̂ = v / (1-β₂ᵗ)            # Bias correction

θ = θ - α × m̂ / (√v̂ + ε)   # Update with both
```

### The Bias Correction Step

There's a subtlety here that's easy to overlook. At the start of training, m and v are initialised to zero. After one step, they're still mostly zero, even if the gradient is large. This makes early steps too small.

The bias correction (dividing by 1-βᵗ) compensates for this. Early in training, when t is small, βᵗ is close to 1, so we divide by a small number, boosting the values. As training progresses, βᵗ approaches 0, and the correction fades away.

This is why Adam often trains well right from the start — it handles initialisation gracefully.

### Default Hyperparameters

Adam's authors (Kingma and Ba, 2014) suggested:
- **α = 0.001** (learning rate)
- **β₁ = 0.9** (momentum decay)
- **β₂ = 0.999** (RMSprop decay)
- **ε = 10⁻⁸** (numerical stability)

These defaults work surprisingly well across many problems. Adam is often called the "just works" optimizer.

### Watching Adam in Action

On the visualization, Adam (orange) typically shows smooth, direct paths. It has momentum's ability to power through small obstacles and RMSprop's ability to handle varying gradient scales. On the ravine, it doesn't oscillate like vanilla SGD. On the local minima field, it doesn't get trapped as easily.

---

## 5. Comparison at a Glance

| Aspect | Vanilla SGD | Momentum | RMSprop | Adam |
|--------|-------------|----------|---------|------|
| **Memory** | None | 1 buffer (velocity) | 1 buffer (squared grad avg) | 2 buffers (m and v) |
| **Per-step cost** | Lowest | Low | Low | Slightly higher |
| **Hyperparameters** | α only | α, β | α, ρ, ε | α, β₁, β₂, ε |
| **Handles ravines** | Poorly (oscillates) | Well | Moderately | Well |
| **Escapes local minima** | Poorly | Well | Moderately | Well |
| **Adaptive per-parameter** | No | No | Yes | Yes |
| **Good defaults exist** | No | Sort of | Sort of | Yes |
| **Typical use** | Research, fine-tuning | When Adam fails | RNNs, non-stationary | Default choice |

### When to Use Each

**Start with Adam**. It's the default for good reason — it handles most situations competently without much tuning.

**Try SGD with momentum** if:
- You need the absolute best final performance (Adam can converge to slightly worse solutions)
- You're fine-tuning a pretrained model
- You're doing research and want to understand behaviour precisely

**Consider RMSprop** for:
- Recurrent neural networks (historically preferred, though Adam often works too)
- Problems where the loss landscape shifts during training

**Use vanilla SGD** for:
- Educational purposes (understanding the baseline)
- When you want maximum control and are willing to tune carefully

---

## 6. Why This Matters for ML/AI

### Training Dynamics Are Shaped by Your Optimizer

The choice of optimizer isn't just about speed — it affects *what* your model learns. Different optimizers explore the loss landscape differently, and can converge to different solutions.

Some research suggests that the "sharp minima" found by adaptive optimizers (like Adam) may generalise worse than the "flat minima" found by SGD with momentum. This is why some practitioners train with Adam initially (for fast progress) then switch to SGD for final tuning.

### Diagnosing Training Problems

Understanding optimizers helps you debug:

- **Loss oscillating wildly?** Learning rate is too high. Or, if using vanilla SGD, try momentum.
- **Loss decreasing but painfully slowly?** Learning rate might be too low, or you're stuck in a plateau. Adaptive optimizers handle plateaus better.
- **Loss stuck after rapid initial progress?** Might have hit a local minimum. Momentum helps escape. Or, counter-intuitively, your learning rate might be too *low* to jump out.
- **Some weights exploding, others dead?** Different parameters need different learning rates. Switch to an adaptive optimizer.

### The Visualisation as a Diagnostic Tool

What you're seeing in the Three.js visualization is exactly what happens during neural network training — just in two dimensions instead of millions. The same behaviours apply:

- Vanilla SGD's oscillations in ravines → why training CNNs without momentum is painful
- Momentum's ability to escape dips → why it helps reach better minima
- RMSprop's parameter-specific adaptation → why it's good for sparse gradients
- Adam's smooth convergence → why it's the default

---

## The Bigger Picture

Optimizers are one of the "magic ingredients" that made deep learning practical. The mathematics behind them — exponential moving averages, adaptive scaling, bias correction — are elegant solutions to real problems discovered through trial and error.

But don't let the formulas intimidate you. At their core:

- **Momentum** = "remember which way I've been going"
- **RMSprop** = "scale steps by how much each parameter usually changes"
- **Adam** = "do both"

Watch the visualization. See how they behave differently on different terrains. That intuition will serve you better than memorising equations.

---

## Next Steps

Now that you understand *how* these optimizers work, you're ready to explore:
- **Learning rate schedules** — changing α during training
- **Weight decay and regularisation** — preventing overfitting
- **Batch size effects** — how the amount of data per step interacts with learning rate

But for now, play with the visualization. Crank up momentum and watch it overshoot. Drop the learning rate and watch everything slow down. Build intuition through experimentation.
