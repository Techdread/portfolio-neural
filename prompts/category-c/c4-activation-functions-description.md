# C4: Activation Functions Gallery — Educational Explanation Prompt

## Topic
Activation Functions — The Non-Linear Heart of Neural Networks

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see sigmoid, tanh, ReLU, Leaky ReLU, and GELU side-by-side with both function and derivative plots.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Activation Functions — The Non-Linear Heart of Neural Networks

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see sigmoid, tanh, ReLU, Leaky ReLU, and GELU side-by-side with both function and derivative plots.

**Prerequisites the learner should already understand**:
- What a function does
- Derivatives as slopes (B1)
- Forward pass (C1)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand why non-linearity is essential (linear networks collapse)
2. Know the major activation functions by shape and behavior
3. Understand the derivative of each activation (crucial for backprop)
4. Know which activations to use when and why
5. Understand vanishing gradient problem with certain activations

**Required Sections**:
1. **Why Non-Linearity?** — Without it, any deep network = one linear layer
2. **The Activation Zoo** — For each function:
   - **Sigmoid (σ)**: formula, shape, range (0,1), use cases, problems
   - **Tanh**: formula, shape, range (-1,1), centered, better than sigmoid
   - **ReLU**: formula, shape, range [0,∞), computational efficiency, dead neurons
   - **Leaky ReLU**: formula, addresses dead neuron problem, small negative slope
   - **GELU**: formula (approximate), smooth, used in transformers
3. **Derivatives Matter**:
   - Sigmoid derivative: σ(x)(1-σ(x)), max at 0.25!
   - Tanh derivative: 1-tanh²(x), max at 1
   - ReLU derivative: 0 or 1, no vanishing!
   - Why derivative matters: backprop multiplies through these
4. **The Vanishing Gradient Problem**:
   - Sigmoid/tanh squash gradients toward 0
   - Many layers = many small multiplications → gradient vanishes
   - ReLU family avoids this (gradient is 0 or 1)
5. **Choosing Activations**:
   - Hidden layers: ReLU, Leaky ReLU, GELU
   - Output layer: depends on task (sigmoid for binary, softmax for multi-class, linear for regression)
6. **Modern Trends** — GELU in transformers, Swish/SiLU gaining popularity

**Tone**: Practical focus on when to use what. Don't just list formulas—explain implications.

**Length**: Approximately 2000-2500 words covering all major activations thoroughly.
```
