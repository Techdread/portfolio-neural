# C1: Forward Pass Step-by-Step — Educational Explanation Prompt

## Topic
The Neural Network Forward Pass — Step by Step

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see data flowing through layers: input → weighted sum → activation → output, with actual numbers displayed.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Neural Network Forward Pass — Step by Step

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see data flowing through layers: input → weighted sum → activation → output, with actual numbers displayed.

**Prerequisites the learner should already understand**:
- Vectors and dot products (A1)
- Matrix multiplication (A2)
- What a function does (maps input to output)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand a neural network as layers of computations
2. Know what happens at each neuron: weighted sum + bias + activation
3. Trace exact numbers through a simple network
4. Understand why matrix multiplication handles all neurons in a layer at once
5. Know the difference between weights, biases, and activations

**Required Sections**:
1. **What is a Forward Pass?** — Data entering, flowing through, result coming out
2. **The Single Neuron**:
   - Receives multiple inputs
   - Each input multiplied by a weight
   - Sum all weighted inputs
   - Add a bias
   - Apply activation function
   - Formula: output = activation(w₁x₁ + w₂x₂ + ... + wₙxₙ + b)
3. **Why Weights and Biases?**:
   - Weights: importance of each input
   - Bias: shift the decision threshold
4. **Activation Functions** — Non-linearity introduction (brief, detailed in C4)
5. **From Neuron to Layer**:
   - A layer = many neurons receiving same inputs
   - Matrix multiplication does all neurons at once
   - output = activation(W · input + b)
6. **Multiple Layers**:
   - Output of layer 1 becomes input to layer 2
   - Stacking layers = composing functions
7. **Worked Example with Numbers**:
   - 2 inputs, 2 hidden neurons, 1 output
   - Show EVERY number at EVERY step
8. **Why This Matters for ML/AI**:
   - Prediction = one forward pass
   - Inference time = sum of layer computations
   - Understanding forward pass is prerequisite for backprop

**Tone**: Very concrete. Use actual numbers everywhere. Make the math tangible.

**Length**: Approximately 2000-2500 words with detailed worked example.
```
