# B6: Sum Rule & Linearity — Educational Explanation Prompt

## Topic
Sum Rule and Linearity of Differentiation

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see derivatives distributing over addition — a simple but foundational concept.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Sum Rule and Linearity of Differentiation

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see derivatives distributing over addition — a simple but foundational concept.

**Prerequisites the learner should already understand**:
- Derivatives of single functions (B1)
- What adding functions means: h(x) = f(x) + g(x)

**Learning Objectives** — After reading this explanation, the learner should:
1. Know the sum rule: (f + g)' = f' + g'
2. Know the constant multiple rule: (cf)' = c · f'
3. Understand linearity: derivative of linear combination = linear combination of derivatives
4. See why this makes differentiation "nice"

**Required Sections**:
1. **Adding Functions** — h(x) = f(x) + g(x) means adding heights at each x
2. **The Sum Rule** — (f + g)' = f' + g'
   - Intuition: slopes add up
   - If f is increasing by 2 and g is increasing by 3, total is increasing by 5
3. **The Constant Multiple Rule** — (cf)' = c · f'
   - Scaling a function scales its derivative
   - Twice as steep everywhere
4. **Difference Rule** — (f - g)' = f' - g' (just sum rule with negative)
5. **Linearity Property**:
   - Derivative is a "linear operator"
   - d/dx[af(x) + bg(x)] = a·f'(x) + b·g'(x)
6. **Why This is Wonderful**:
   - Break complex functions into simpler pieces
   - Differentiate pieces separately
   - Combine the results
7. **Why This Matters for ML/AI**:
   - Neural network outputs are sums of weighted inputs
   - Gradients distribute over additions
   - Makes backprop through sum nodes trivial
   - Residual connections: gradient flows through addition unchanged

**Tone**: Keep it simple. This is foundational scaffolding for harder rules.

**Length**: Approximately 1000-1300 words. Brief and clear.
```
