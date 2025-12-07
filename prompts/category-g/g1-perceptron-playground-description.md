# G1: Perceptron Playground — Educational Explanation Prompt

## Topic
The Perceptron — The Simplest Neural Network

## Context
This is part of an interactive Three.js visualization portfolio. The learner will drag points around and watch a perceptron find the separating hyperplane, also learning about its linear limitations.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Perceptron — The Simplest Neural Network

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will drag points around and watch a perceptron find the separating hyperplane, also learning about its linear limitations.

**Prerequisites the learner should already understand**:
- Coordinates and points in 2D
- What a line equation is (ax + by + c = 0)
- Basic idea of classification

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the perceptron as a binary linear classifier
2. Know the perceptron algorithm (classify, check, update)
3. Visualize the decision boundary as a line
4. Understand linear separability
5. Know the XOR problem (why perceptrons have limits)

**Required Sections**:
1. **Historical Context** — Rosenblatt's perceptron (1958), excitement, then AI winter
2. **The Perceptron Model**:
   - Inputs × weights + bias
   - Sum = weighted combination
   - Activation: sign function (output +1 or -1)
   - Formula: y = sign(w·x + b)
3. **The Decision Boundary**:
   - Where w·x + b = 0
   - A line (or hyperplane in higher dimensions)
   - Points on one side = class A, other side = class B
4. **The Learning Algorithm**:
   - Initialize weights randomly
   - For each point: classify, check if correct
   - If wrong: update weights toward correct answer
   - Repeat until all points correct (if linearly separable)
5. **Linear Separability**:
   - Some datasets can be separated by a line
   - Perceptron guaranteed to converge for these
   - But some datasets CANNOT be linearly separated
6. **The XOR Problem**:
   - XOR: (0,0)→0, (0,1)→1, (1,0)→1, (1,1)→0
   - No line can separate these classes
   - Famous limitation that led to multi-layer networks
7. **Why This Matters for ML/AI**:
   - Foundation for understanding neural networks
   - Shows why we need multiple layers
   - The learning algorithm is gradient-free but inspired gradient descent

**Tone**: Historical but practical. Make the limitations feel like a cliffhanger leading to deep learning.

**Length**: Approximately 1600-2000 words with clear XOR explanation.
```
