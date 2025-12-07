# B5: Product Rule — Educational Explanation Prompt

## Topic
The Product Rule — Derivative of Multiplied Functions

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see the area of a rectangle analogy: d(uv) = u·dv + v·du with both terms animated.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Product Rule — Derivative of Multiplied Functions

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see the area of a rectangle analogy: d(uv) = u·dv + v·du with both terms animated.

**Prerequisites the learner should already understand**:
- Derivatives of single functions (B1)
- What multiplication of functions means: h(x) = f(x) × g(x)

**Learning Objectives** — After reading this explanation, the learner should:
1. Know the product rule formula: (fg)' = f'g + fg'
2. Understand the geometric interpretation (rectangle area)
3. Apply the product rule to compute derivatives
4. Know when and why the product rule is needed

**Required Sections**:
1. **The Setup** — Two functions multiplied: h(x) = f(x) · g(x)
2. **Why Not Just Multiply Derivatives?** — Show counterexample: (f·g)' ≠ f'·g'
3. **The Rectangle Analogy**:
   - Rectangle with width f(x) and height g(x)
   - Area = f(x) · g(x)
   - When x changes, both dimensions change!
   - Change in area = f·Δg + g·Δf + Δf·Δg (third term vanishes)
4. **The Product Rule Formula**:
   - (fg)' = f'g + fg' (Leibniz: d(uv) = u·dv + v·du)
   - "First times derivative of second, plus second times derivative of first"
5. **Worked Examples**:
   - h(x) = x² · sin(x)
   - h(x) = e^x · x
6. **Common Mistakes** — Don't just multiply the derivatives
7. **Why This Matters for ML/AI**:
   - Gating mechanisms: sigmoid · hidden state (LSTMs)
   - Attention: softmax weights × values
   - Loss functions with regularization terms
   - When backprop encounters multiplications

**Tone**: Focus on the rectangle intuition. Make the formula memorable with mnemonics.

**Length**: Approximately 1200-1500 words. Concise but thorough.
```
