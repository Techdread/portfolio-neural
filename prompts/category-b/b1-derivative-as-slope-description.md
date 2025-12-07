# B1: Derivative as Slope — Educational Explanation Prompt

## Topic
The Derivative as Slope — Understanding Rate of Change

## Context
This is part of an interactive Three.js visualization portfolio teaching neural network mathematics. The learner will see an interactive function with a draggable point showing the tangent line.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Derivative as Slope — Understanding Rate of Change

**Context**: This is part of an interactive Three.js visualization portfolio teaching neural network mathematics. The learner will see an interactive function with a draggable point showing the tangent line.

**Prerequisites the learner should already understand**:
- Basic coordinate systems (x-y graphs)
- What a function is (input → output)
- Slope of a straight line (rise/run)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the derivative as "instantaneous rate of change"
2. Visualize the derivative as the slope of the tangent line
3. Understand the limit definition intuitively (secant → tangent)
4. Read derivative notation (f'(x), df/dx, dy/dx)
5. Know basic derivative rules (power rule, constant rule)
6. Connect derivatives to gradient descent optimization

**Required Sections**:
1. **Slope Recap** — Rise over run for straight lines
2. **The Problem with Curves** — Slope changes at every point
3. **The Secant Line Approach** — Average rate of change between two points
4. **The Key Insight** — Move the points closer together, secant → tangent
5. **The Limit Definition** — f'(x) = lim(h→0) [f(x+h) - f(x)] / h
   - Explain without heavy formalism
   - "What slope do we approach as the gap shrinks to zero?"
6. **Tangent Line** — The line that just "touches" the curve at one point
7. **Derivative Notation**:
   - f'(x): "f prime of x"
   - df/dx: "derivative of f with respect to x"
   - dy/dx: Leibniz notation
8. **Basic Rules** (intuitive, not proof-heavy):
   - Constant: derivative is 0 (flat line)
   - Power rule: x^n → nx^(n-1)
   - Sum rule: derivative of sum = sum of derivatives
9. **Why This Matters for ML/AI**:
   - Loss functions are curves we want to minimize
   - Derivative tells us which direction is "downhill"
   - Gradient descent: step in direction opposite to derivative
   - Every neural network weight is adjusted based on derivatives

**Tone**: Build intuition progressively. Use animations described in words. Make the limit definition feel natural, not scary.

**Length**: Approximately 1800-2200 words with clear progression from slope to derivative.
```
