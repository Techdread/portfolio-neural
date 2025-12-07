# F3: Weight Initialisation Comparison — Educational Explanation Prompt

## Topic
Weight Initialization — Starting Training Right

## Context
This is part of an interactive Three.js visualization portfolio. The learner will compare Xavier, He, and random initialization, seeing how activation distributions evolve through layers over epochs.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Weight Initialization — Starting Training Right

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will compare Xavier, He, and random initialization, seeing how activation distributions evolve through layers over epochs.

**Prerequisites the learner should already understand**:
- Neural network basics (C1)
- Activation functions (C4)
- Gradient flow (F2)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand why initialization matters
2. Know the problem with naive random initialization
3. Understand Xavier initialization and when to use it
4. Understand He initialization and when to use it
5. See how initialization affects activation distributions

**Required Sections**:
1. **Why Initialization Matters**:
   - Too small weights: signals vanish through layers
   - Too large weights: signals explode or saturate
   - Gradient flow depends on activation magnitudes
2. **Naive Random Initialization**:
   - Just random numbers
   - Usually causes problems
   - Activations shrink or explode layer by layer
3. **The Variance Problem**:
   - Output variance depends on input variance × weight variance × fan_in
   - Want output variance ≈ input variance (stable)
4. **Xavier/Glorot Initialization**:
   - Scale weights by 1/√(fan_in + fan_out)
   - Keeps variance stable for linear/tanh/sigmoid
   - Default for most activations
5. **He/Kaiming Initialization**:
   - Scale weights by √(2/fan_in)
   - Designed for ReLU (which zeros half the values)
   - Use with ReLU and variants
6. **Practical Guidelines**:
   - Use He for ReLU/Leaky ReLU
   - Use Xavier for tanh/sigmoid
   - Modern frameworks handle this automatically
7. **Why This Matters for ML/AI**:
   - Bad initialization = training failure or slow convergence
   - Good initialization = faster, more stable training
   - One of the key breakthroughs for deep learning

**Tone**: Practical focus. Show the problem, then the solution. Don't dwell on derivations.

**Length**: Approximately 1500-1800 words with clear recommendations.
```
