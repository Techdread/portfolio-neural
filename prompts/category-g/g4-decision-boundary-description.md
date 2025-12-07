# G4: Decision Boundary Evolution — Educational Explanation Prompt

## Topic
Decision Boundaries — Watching a Classifier Learn

## Context
This is part of an interactive Three.js visualization portfolio. The learner will watch classifier boundaries form during training on 2D data.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Decision Boundaries — Watching a Classifier Learn

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will watch classifier boundaries form during training on 2D data.

**Prerequisites the learner should already understand**:
- Classification basics
- Neural networks (C1)
- Gradient descent (D1)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand decision boundaries as classification regions
2. See how boundaries evolve during training
3. Know how model complexity affects boundary shape
4. Recognize underfitting, good fit, and overfitting in boundaries

**Required Sections**:
1. **What is a Decision Boundary?** — The frontier between class regions
2. **Linear Boundaries**:
   - Single line/plane separating classes
   - Logistic regression, perceptron
   - Limited to linearly separable problems
3. **Non-Linear Boundaries**:
   - Neural networks with hidden layers
   - Can curve around data
   - More layers = more complex boundaries
4. **Boundary Evolution**:
   - Start: random boundary (based on initial weights)
   - Training: boundary shifts to reduce errors
   - End: boundary separates classes (hopefully)
5. **Complexity and Capacity**:
   - Simple model: smooth boundaries
   - Complex model: wiggly, detailed boundaries
   - Too complex: overfits, follows noise
6. **Reading Boundaries**:
   - Wide margins = confident regions
   - Narrow regions = uncertain
   - Wisps and tendrils = possible overfitting
7. **Why This Matters for ML/AI**:
   - Visualizing what the model "learned"
   - Debugging classification problems
   - Understanding model capacity

**Tone**: Focus on the visual evolution story. Make training feel like watching a picture develop.

**Length**: Approximately 1400-1700 words with vivid descriptions of boundary evolution.
```
