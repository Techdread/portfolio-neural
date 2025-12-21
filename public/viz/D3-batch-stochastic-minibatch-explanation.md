# Batch, Stochastic, and Mini-batch Gradient Descent

## The Noise-Accuracy Trade-off

So far, we've treated gradient descent as if there's one clean gradient pointing downhill. But in real machine learning, the gradient depends on your *data* — and how much data you use to estimate that gradient changes everything.

Use all your data? You get a perfect gradient but wait forever. Use one sample? Lightning fast but wildly noisy. The sweet spot in the middle is where all of modern deep learning lives.

---

## 1. The Dataset Setting

Before diving into variants, let's clarify what we're actually computing.

In machine learning, the loss function measures how wrong your model is *on average* across your dataset:

```
L(θ) = (1/N) Σᵢ Lᵢ(θ)
```

This says: the total loss is the average of individual losses for each of the N data points. The gradient follows the same pattern — it's the average of individual gradients:

```
∇L(θ) = (1/N) Σᵢ ∇Lᵢ(θ)
```

Now the question becomes: do you need to compute *all* N individual gradients to take one step? Or can you estimate the average from fewer samples?

This is the core tension. More samples give a better estimate of the true gradient. Fewer samples mean faster updates. Different variants make different trade-offs.

---

## 2. Batch (Full) Gradient Descent

### How It Works

Batch gradient descent computes the gradient using **every single data point** before taking one step. If you have 50,000 training images, you process all 50,000 to update your weights once.

```
For each epoch:
    gradient = average gradient over ALL N samples
    θ = θ - α · gradient
```

### The Pros

**Accurate gradient**: You're computing the true gradient of the loss function, not an estimate. The direction you step is exactly the direction of steepest descent.

**Smooth convergence**: In the visualization, watch how batch descent produces clean, direct paths. No zigzagging, no noise — just steady progress.

**Deterministic**: Same starting point, same path, every time. This makes debugging easier.

### The Cons

**Painfully slow**: One step requires processing your entire dataset. With millions of samples, each update takes ages. You might only manage a few updates per hour.

**Memory hungry**: To vectorise efficiently, you often need the whole dataset (or large chunks) in memory simultaneously. This can exceed GPU memory.

**Gets stuck easily**: That smooth, noise-free path? It follows the gradient precisely into local minima and stays there. No randomness means no escape.

### When It's Used

Rarely, in modern deep learning. Batch gradient descent is primarily a teaching tool — useful for understanding the ideal case before adding complexity. You might see it in small-scale optimisation problems or convex settings where local minima aren't a concern.

---

## 3. Stochastic Gradient Descent (SGD)

### How It Works

Stochastic gradient descent swings to the opposite extreme: compute the gradient from **one randomly chosen sample**, then immediately update.

```
For each epoch:
    Shuffle dataset
    For each sample xᵢ:
        gradient = gradient for sample i only
        θ = θ - α · gradient
```

With 50,000 images, you now make 50,000 weight updates per epoch instead of one.

### The Pros

**Blazingly fast updates**: Each step requires processing just one sample. You can update thousands of times per second.

**Memory efficient**: Only one sample needs to be in memory at a time. Datasets of any size become tractable.

**Escapes local minima**: Here's the magic — that noisy gradient isn't a bug, it's a feature. The randomness lets the optimiser jump out of shallow local minima and saddle points. In the visualization, watch the SGD path zigzag wildly but ultimately explore more of the surface.

**Online learning**: Can learn from streaming data, updating as new samples arrive.

### The Cons

**Extremely noisy**: The gradient from one sample is a terrible estimate of the true gradient. It points vaguely in the right direction on average, but any individual step might be completely wrong.

**Erratic path**: The descent path looks drunk. Two steps forward, one step sideways, half a step back. Progress happens, but it's hard to see in the moment.

**Never truly converges**: Because every step is noisy, you never settle into a minimum — you bounce around it forever. You need to decay the learning rate to eventually stop.

**Wastes hardware**: Modern GPUs are designed for parallel operations on batches. Processing one sample at a time leaves most of the chip idle.

### The Noise Advantage

This deserves emphasis: SGD's noise is genuinely helpful. Research shows that stochastic methods find *better* minima than batch methods. The noise acts like a form of regularisation, preventing the model from overfitting to every detail of the training data.

Think of it like shaking a box of sand to find a stable arrangement versus carefully placing each grain. The shaking finds robust solutions.

---

## 4. Mini-batch Gradient Descent

### The Practical Middle Ground

Mini-batch gradient descent combines the best of both worlds: compute the gradient using a **subset of data** — typically 32 to 512 samples — then update.

```
For each epoch:
    Shuffle dataset
    Split into mini-batches of size B
    For each mini-batch:
        gradient = average gradient over B samples
        θ = θ - α · gradient
```

With 50,000 images and batch size 64, you make about 780 updates per epoch. Not one, not 50,000, but a sensible middle ground.

### Why Mini-batch Wins

**Good gradient estimates**: Averaging over 64 samples gives a much better estimate than one sample, while still being noisy enough to escape local minima.

**Hardware utilisation**: GPUs excel at parallel matrix operations. A batch of 64 images can be processed nearly as fast as a single image, thanks to vectorisation. You get 64x the information for roughly 1x the time.

**Memory balance**: 64 samples fit comfortably in GPU memory, even for large models and high-resolution images.

**Regularisation effect**: The residual noise from using subsets (rather than full data) still provides the beneficial regularisation effect, just more controlled.

### The Universal Standard

When practitioners say "SGD" today, they almost always mean mini-batch gradient descent. True single-sample SGD is rarely used. This terminology confusion is worth remembering:

- **Theoretical SGD**: One sample per step
- **Practical "SGD"**: Mini-batch gradient descent

The optimiser you'll see in frameworks like PyTorch or TensorFlow, labeled `SGD`, defaults to mini-batch operation.

---

## 5. Batch Size Effects

Batch size is a hyperparameter with surprising depth. It's not just about speed — it affects what your model learns.

### Larger Batches

- **More accurate gradients**: Less noise, more stable training
- **Faster wall-clock time**: Better GPU utilisation
- **Higher memory usage**: May not fit on your GPU
- **Worse generalisation**: Counter-intuitively, very large batches can lead to models that perform worse on new data. They find "sharp" minima that don't generalise.

### Smaller Batches

- **Noisier gradients**: More regularisation effect
- **More updates per epoch**: More opportunities to adjust
- **Lower memory usage**: Fits on smaller GPUs
- **Better generalisation**: Often finds "flat" minima that transfer well to new data

### Common Choices

| Batch Size | Typical Use Case |
|------------|-----------------|
| 1 | True SGD (rare) |
| 16-32 | Limited GPU memory, want more noise |
| 64-128 | General-purpose default |
| 256-512 | Large-scale training with big GPUs |
| 1000+ | Distributed training across many GPUs |

### The Learning Rate Connection

A crucial interaction: when you increase batch size, you often need to increase learning rate. The intuition is that larger batches give more confident gradient estimates, so you can take bigger steps. A common rule: scale learning rate linearly with batch size (double batch, double LR).

---

## 6. What You'll See in the Visualization

The three variants produce dramatically different descent paths on the same surface:

**Batch GD** traces a smooth curve directly toward the minimum. It's elegant but slow — watch the step counter. Each step requires processing the full dataset.

**Stochastic GD** zigzags wildly. The path looks chaotic, but notice how it explores the surface more broadly. It might stumble into regions that batch GD would never visit. The noise is visible as jitter in the direction.

**Mini-batch GD** shows controlled wobble — more stable than pure SGD, more exploratory than batch. This is the practical compromise you'll use in real training.

Try adjusting the batch size slider. Watch how larger batches smooth the path toward batch GD behaviour, while smaller batches add SGD-like noise.

---

## 7. Why This Matters for ML/AI

### Mini-batch Is Universal

Virtually every neural network you'll train uses mini-batch gradient descent. Understanding why — the balance of speed, accuracy, and beneficial noise — helps you make informed choices about batch size.

### Batch Size Is a Hyperparameter

It's not just a hardware constraint. The batch size you choose affects:
- Training speed (larger is faster per epoch)
- Memory requirements (larger needs more)
- Generalisation performance (often worse with very large batches)
- Optimal learning rate (scales with batch size)

### Noise as Regularisation

One of the deeper insights in deep learning: the noise from stochastic methods isn't just tolerated, it's beneficial. It prevents overfitting and helps find robust solutions. This is why even with infinite compute, you wouldn't necessarily want true batch gradient descent.

---

## The Terminology Trap

A final note on confusing terminology that trips up many learners:

- When papers say **"SGD"**, they usually mean mini-batch with momentum
- When tutorials say **"batch"**, they sometimes mean mini-batch
- When frameworks offer **"batch_size"**, they mean mini-batch size
- True single-sample stochastic updates are called **"online learning"**

The field's vocabulary evolved messily. Just remember: in practice, everything is mini-batch, regardless of what it's called.

---

## Next Steps

With batch variants understood, you're ready to explore:
- **Momentum and Adam** — techniques that improve upon basic mini-batch SGD
- **Learning rate schedules** — how to adjust the step size during training
- **Gradient accumulation** — simulating larger batches with limited memory

The core insight to carry forward: gradient descent is always an estimation game. How much data you use to estimate the gradient shapes everything about training.
