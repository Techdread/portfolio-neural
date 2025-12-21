# C6: Softmax and Cross-Entropy — From Scores to Probabilities to Loss

## The Classification Pipeline

When a neural network classifies an image as "cat," "dog," or "bird," what actually happens inside? The network doesn't output the word "cat." It outputs numbers—raw scores for each possible class. These scores need to become probabilities, and those probabilities need to become a single number measuring how wrong the prediction was.

The pipeline looks like this:

```
Raw Scores (Logits) → Softmax → Probabilities → Cross-Entropy → Loss
     [2.0, 1.0, 0.1]     →     [0.659, 0.242, 0.099]     →     0.42
```

Each step has a purpose. Softmax turns arbitrary numbers into probabilities. Cross-entropy measures how far those probabilities are from the truth. Together, they form the standard ending for classification networks.

---

## What Are Logits?

The last layer of a classification network produces **logits**—raw, unnormalized scores. One score per class.

```
Network output for 3-class problem:
  Cat:  2.0
  Dog:  1.0
  Bird: 0.1
```

These numbers have no restrictions:
- They can be positive, negative, or zero
- They can be any magnitude
- They don't sum to anything special

Logits encode the network's relative preferences. A higher score means the network favors that class. Cat (2.0) is preferred over Dog (1.0), which is preferred over Bird (0.1).

But logits aren't probabilities. We can't say "the model is 2.0% sure it's a cat"—that doesn't make sense. We need to convert these scores into proper probabilities that sum to 1.

---

## The Softmax Function

Softmax transforms logits into probabilities:

```
softmax(zᵢ) = e^zᵢ / Σⱼ e^zⱼ
```

In words: take e raised to each score, then normalize by dividing by the sum of all exponentials.

**Step-by-step example:**

Starting with logits [2.0, 1.0, 0.1]:

**Step 1: Compute exponentials**
```
e^2.0 = 7.389
e^1.0 = 2.718
e^0.1 = 1.105
```

**Step 2: Sum the exponentials**
```
7.389 + 2.718 + 1.105 = 11.212
```

**Step 3: Divide each by the sum**
```
Cat:  7.389 / 11.212 = 0.659  (65.9%)
Dog:  2.718 / 11.212 = 0.242  (24.2%)
Bird: 1.105 / 11.212 = 0.099  (9.9%)
```

**Verify:** 0.659 + 0.242 + 0.099 = 1.000 ✓

The logits [2.0, 1.0, 0.1] become probabilities [0.659, 0.242, 0.099]. The model is 65.9% confident it's a cat.

---

## Why Exponentials?

The exponential function has special properties that make it perfect for this job:

**1. Always positive:** e^x > 0 for any x. Even e^(-100) is a tiny positive number, never zero or negative. This guarantees all probabilities are positive.

**2. Preserves ordering:** If z₁ > z₂, then e^z₁ > e^z₂. The class with the highest logit gets the highest probability.

**3. Amplifies differences:** The exponential is a convex function that grows rapidly. Small differences in logits become larger differences in probabilities.

Consider logits [3.0, 2.9, 2.8]—very close scores:

```
e^3.0 = 20.09
e^2.9 = 18.17
e^2.8 = 16.44

Probabilities: [0.367, 0.332, 0.301]
```

Now consider logits [5.0, 2.0, 1.0]—spread apart:

```
e^5.0 = 148.4
e^2.0 = 7.39
e^1.0 = 2.72

Probabilities: [0.936, 0.047, 0.017]
```

When the network is confident (large differences in logits), softmax produces sharp probability distributions. When uncertain (similar logits), it produces softer distributions.

---

## Why Not Just Normalize Directly?

You might wonder: why not simply divide each logit by their sum?

```
Naive normalization of [2.0, 1.0, 0.1]:
Sum = 3.1
Probabilities: [0.645, 0.323, 0.032]
```

This fails for two reasons:

**1. Negative logits break it:**
```
Logits: [2.0, -1.0, -3.0]
Sum = -2.0
"Probabilities": [-1.0, 0.5, 1.5]  ← Negative! Greater than 1!
```

**2. Can't differentiate argmax:**
The function argmax(z) = "pick the biggest" isn't differentiable. You can't compute gradients through a hard choice. Softmax is a smooth, differentiable approximation to argmax.

---

## Temperature: Controlling Confidence

Softmax has an optional parameter called temperature (T):

```
softmax(zᵢ; T) = e^(zᵢ/T) / Σⱼ e^(zⱼ/T)
```

Temperature controls how "sharp" or "soft" the output distribution is.

**Low temperature (T = 0.5):** Dividing by 0.5 doubles the logits. Differences are amplified. The distribution becomes sharper—more confident.

**High temperature (T = 2.0):** Dividing by 2 halves the logits. Differences are reduced. The distribution becomes softer—less confident.

**T → 0:** Approaches argmax. One class gets probability 1, others get 0.

**T → ∞:** Approaches uniform distribution. All classes get equal probability.

Example with logits [2.0, 1.0, 0.0]:

| Temperature | Probabilities |
|-------------|---------------|
| T = 0.5 | [0.844, 0.114, 0.042] |
| T = 1.0 | [0.659, 0.242, 0.099] |
| T = 2.0 | [0.506, 0.307, 0.187] |

Temperature is used during inference to control randomness in text generation and other sampling tasks.

---

## Cross-Entropy Loss

Now we have probabilities. How do we measure how wrong they are?

**Cross-entropy loss** compares the predicted probability distribution to the true distribution:

```
L = -Σᵢ yᵢ · log(pᵢ)
```

Where:
- yᵢ is the true label (1 for correct class, 0 for others)
- pᵢ is the predicted probability for class i

For classification with one-hot labels, this simplifies dramatically. If the true class is "Cat" (y = [1, 0, 0]):

```
L = -[1·log(p_cat) + 0·log(p_dog) + 0·log(p_bird)]
  = -log(p_cat)
```

**Only the correct class matters!** Cross-entropy loss is simply the negative log of the probability assigned to the true class.

---

## The Log Penalty

The negative log function creates a harsh penalty structure:

```
p_correct = 0.99  →  Loss = -log(0.99) = 0.01   (tiny loss)
p_correct = 0.90  →  Loss = -log(0.90) = 0.11
p_correct = 0.50  →  Loss = -log(0.50) = 0.69
p_correct = 0.10  →  Loss = -log(0.10) = 2.30
p_correct = 0.01  →  Loss = -log(0.01) = 4.61   (huge loss!)
p_correct = 0.001 →  Loss = -log(0.001) = 6.91  (enormous!)
```

The pattern is clear:
- **Confident and correct:** Probability near 1 → loss near 0
- **Uncertain:** Probability around 0.5 → moderate loss
- **Confident and wrong:** Probability near 0 → loss explodes

This asymmetry is the genius of cross-entropy. It doesn't just reward correct predictions—it *severely punishes* confident wrong predictions.

---

## Why the Harsh Penalty Matters

Imagine a model predicting the correct class with probability 0.01 (1%). The loss is 4.61.

To understand this magnitude: if another sample is predicted correctly with probability 0.99 (loss = 0.01), you'd need **461 such correct predictions** to balance out the one confident mistake.

This forces the network to be calibrated. It can't get away with being overconfident on some samples while being correct on average. Every confident mistake is catastrophically expensive.

**Practical example:**

Medical diagnosis with 100 patients. The model correctly identifies 99 healthy patients with 99% confidence (loss ≈ 0.01 each). But it confidently predicts the one sick patient is healthy with 99% confidence.

```
99 correct predictions: 99 × 0.01 = 0.99 total loss
1 confident mistake: -log(0.01) = 4.61 loss

Average loss = (0.99 + 4.61) / 100 = 0.056
```

That one mistake dominates the average! The network is strongly incentivized to not be overconfident, especially on edge cases.

---

## Worked Example: Complete Pipeline

Let's trace through the full pipeline.

**Scenario:** 3-class classification (Cat, Dog, Bird). True label is Dog.

**Step 1: Network outputs logits**
```
Logits: [1.0, 3.0, 0.5]
        Cat   Dog  Bird
```

**Step 2: Apply softmax**
```
e^1.0 = 2.718
e^3.0 = 20.086
e^0.5 = 1.649

Sum = 24.453

Probabilities:
  Cat:  2.718 / 24.453 = 0.111 (11.1%)
  Dog:  20.086 / 24.453 = 0.821 (82.1%)
  Bird: 1.649 / 24.453 = 0.067 (6.7%)
```

**Step 3: Compute cross-entropy loss**

True label is Dog, so:
```
L = -log(p_dog) = -log(0.821) = 0.197
```

The loss is relatively low (0.197) because the model correctly assigned high probability (82.1%) to the true class.

**What if the model was wrong?**

Same logits, but true label is Bird:
```
L = -log(p_bird) = -log(0.067) = 2.70
```

Much higher loss! The model was confident about Dog but the answer was Bird.

---

## Numerical Stability

There's a practical problem with naive softmax computation.

**Overflow:** If logits are large, e^z explodes:
```
e^100 = 2.7 × 10^43  (too big for float32)
e^1000 = Infinity
```

**Underflow:** If logits are very negative, e^z becomes zero:
```
e^-100 = 3.7 × 10^-44  (rounds to 0 in float32)
```

**Solution: Subtract the maximum**

A beautiful property of softmax: subtracting a constant from all logits doesn't change the result.

```
softmax(zᵢ - c) = e^(zᵢ-c) / Σⱼ e^(zⱼ-c)
                = e^zᵢ · e^-c / Σⱼ e^zⱼ · e^-c
                = e^zᵢ / Σⱼ e^zⱼ  (e^-c cancels!)
                = softmax(zᵢ)
```

By choosing c = max(z), we ensure the largest exponent is e^0 = 1, preventing overflow:

```
Logits: [100, 99, 98]
Shifted: [0, -1, -2]
Exponentials: [1, 0.368, 0.135]  ← No overflow!
```

This is the **log-sum-exp trick**, and every deep learning framework uses it automatically.

---

## Combined Softmax-CrossEntropy

In practice, softmax and cross-entropy are computed together for additional stability.

The combined formula:
```
L = -z_correct + log(Σⱼ e^zⱼ)
```

This avoids computing probabilities explicitly, preventing log(0) when a probability underflows to zero.

With the max-subtraction trick:
```
L = -z_correct + max(z) + log(Σⱼ e^(zⱼ - max(z)))
```

PyTorch's `CrossEntropyLoss` and TensorFlow's `softmax_cross_entropy_with_logits` implement this stable version. They take raw logits as input, not probabilities.

**Important:** Never apply softmax yourself before passing to these functions! They expect logits. Applying softmax first and then using cross-entropy loss can cause numerical instability.

---

## Gradient of Cross-Entropy + Softmax

When training, we need the gradient of the loss with respect to logits. The combined softmax + cross-entropy has an elegant gradient:

```
∂L/∂zᵢ = pᵢ - yᵢ
```

That's it! The gradient is simply the predicted probability minus the true label.

**For the correct class:**
```
∂L/∂z_correct = p_correct - 1
```
If p_correct = 0.8, gradient is -0.2. Negative gradient → increase this logit.

**For incorrect classes:**
```
∂L/∂z_wrong = p_wrong - 0 = p_wrong
```
If p_wrong = 0.15, gradient is 0.15. Positive gradient → decrease this logit.

The network learns to increase logits for correct classes and decrease logits for incorrect ones. The magnitude of the update is proportional to how wrong the prediction was.

---

## Why This Matters for ML/AI

Understanding softmax and cross-entropy is essential for several reasons:

**1. Every classification network uses this**

Whether you're classifying images, documents, or tokens, the final layer is almost always softmax + cross-entropy. It's the universal ending.

**2. Debugging training issues**

When loss is NaN or infinite, it's often numerical instability in softmax/cross-entropy. Knowing the internals helps you diagnose:
- NaN loss: likely log(0) somewhere
- Infinite loss: likely overflow in exponentials
- Loss stuck at log(num_classes): model predicting uniform distribution

**3. Understanding model calibration**

Cross-entropy encourages calibrated predictions. A model trained with cross-entropy should output probabilities that reflect true frequencies. If it says "80% cat" on many images, roughly 80% of those should actually be cats.

**4. Temperature tuning**

For generation tasks (text, images), temperature controls diversity. Knowing that it scales logits before softmax helps you tune it appropriately.

**5. Label smoothing**

A common regularization technique changes the target from [1, 0, 0] to [0.9, 0.05, 0.05]. Understanding cross-entropy helps you see why this prevents overconfidence.

---

## Key Takeaways

1. **Logits are raw scores** with no restrictions. They're what the network actually outputs.

2. **Softmax converts logits to probabilities** using exponentials and normalization. Outputs are positive and sum to 1.

3. **Exponentials amplify differences**, making confident predictions sharper.

4. **Cross-entropy loss = -log(p_correct)**. Only the probability assigned to the true class matters.

5. **The log penalty is harsh**: confident wrong predictions are severely punished, while confident correct predictions are barely rewarded.

6. **Numerical stability matters**. Always use the combined, stable implementation provided by your framework.

7. **The gradient is beautiful**: ∂L/∂z = p - y. Predicted minus true. Simple and efficient.

This pipeline—logits through softmax through cross-entropy—is the foundation of classification in deep learning. Understanding it deeply will help you build, debug, and improve any classification model.
