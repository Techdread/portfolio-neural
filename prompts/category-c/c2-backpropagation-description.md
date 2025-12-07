# C2: Backpropagation Walkthrough — Educational Explanation Prompt

## Topic
Backpropagation — Computing Gradients Layer by Layer

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see error gradients flowing backwards with the chain rule at each node, accumulating gradients.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Backpropagation — Computing Gradients Layer by Layer

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see error gradients flowing backwards with the chain rule at each node, accumulating gradients.

**Prerequisites the learner should already understand**:
- Forward pass (C1)
- The chain rule (B4)
- Partial derivatives (B2)
- The gradient as direction of change (B3)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand backprop as "reverse mode differentiation"
2. Know why we compute gradients from output to input
3. Trace gradient computation through a simple network
4. Understand how gradients accumulate at each weight
5. Connect chain rule multiplication to layer-by-layer gradient flow

**Required Sections**:
1. **The Goal of Backprop** — Compute ∂Loss/∂w for every weight w
2. **Why Backwards?** — Efficiency: one backward pass gives ALL gradients
3. **The Chain Rule Connection**:
   - Loss depends on output
   - Output depends on hidden layer
   - Hidden layer depends on weights
   - Chain them together!
4. **Step-by-Step Backprop**:
   - Start with ∂Loss/∂output (how loss changes with output)
   - Compute ∂output/∂hidden (through activation derivative)
   - Multiply through to get ∂Loss/∂hidden
   - Continue backward to inputs and weights
5. **The Local Gradient** — Each node knows its own derivative
6. **Gradient Accumulation** — When one node feeds multiple paths
7. **Worked Example with Numbers**:
   - Same network as C1
   - Show EXACT gradient numbers at each step
   - Final result: gradient for each weight
8. **Why This Matters for ML/AI**:
   - Backprop enables training of deep networks
   - Without it, we couldn't compute gradients efficiently
   - Autodiff libraries (PyTorch, TensorFlow) do this automatically
9. **Common Confusions**:
   - Backprop ≠ gradient descent (backprop computes, GD uses)
   - Why multiply, not add (chain rule)

**Tone**: Match the step-by-step concreteness of C1. Numbers at every step.

**Length**: Approximately 2200-2800 words with detailed worked example matching C1's network.
```
