# B4: Chain Rule Visualiser — Educational Explanation Prompt

## Topic
The Chain Rule — Derivatives of Composed Functions

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see nested functions as a pipeline with derivatives multiplying through — the heart of backpropagation.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Chain Rule — Derivatives of Composed Functions

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see nested functions as a pipeline with derivatives multiplying through — the heart of backpropagation.

**Prerequisites the learner should already understand**:
- Derivatives of basic functions (B1)
- Function composition: f(g(x))
- What multiplication represents

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand function composition as a pipeline/chain
2. Know the chain rule: d/dx[f(g(x))] = f'(g(x)) · g'(x)
3. Visualize derivatives "multiplying through" the chain
4. Understand why chain rule is THE foundation of backpropagation
5. Apply chain rule to multi-step computations

**Required Sections**:
1. **Function Composition Recap** — f(g(x)): "g processes x, then f processes the result"
2. **The Pipeline Metaphor** — Input flows through stages, each transforming it
3. **The Problem** — How does changing x affect the final output?
4. **Intuitive Chain Rule**:
   - If g doubles its input, and f triples its input...
   - Overall effect: 2 × 3 = 6× (derivatives multiply!)
5. **The Chain Rule Formula**:
   - d/dx[f(g(x))] = f'(g(x)) · g'(x)
   - "Derivative of outer times derivative of inner"
6. **Step-by-Step Example**:
   - h(x) = (3x + 1)²
   - Outer: f(u) = u², Inner: g(x) = 3x + 1
   - Work through completely
7. **Multiple Links in the Chain**:
   - f(g(h(x))): just keep multiplying
   - Each derivative evaluated at its input value
8. **Why This Matters for ML/AI**:
   - Neural network = composition of many functions
   - Forward pass: apply functions in sequence
   - Backward pass: multiply derivatives in reverse (backprop!)
   - Loss depends on weights through many layers
   - Chain rule connects loss to each weight
9. **The Computational Graph View** — Nodes are operations, edges are data flow

**Tone**: Make the "multiply through" intuition extremely clear. The pipeline metaphor is key.

**Length**: Approximately 2000-2400 words — this is critical for understanding backprop.
```
