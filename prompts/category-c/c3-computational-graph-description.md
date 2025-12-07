# C3: Computational Graph — Educational Explanation Prompt

## Topic
Computational Graphs — The Structure Behind Autodiff

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see expression trees for functions and watch autodiff traverse them forwards and backwards.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Computational Graphs — The Structure Behind Autodiff

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see expression trees for functions and watch autodiff traverse them forwards and backwards.

**Prerequisites the learner should already understand**:
- Basic operations (add, multiply, etc.)
- Forward and backward pass concepts (C1, C2)
- Chain rule (B4)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand expressions as tree/graph structures
2. Know how autodiff libraries represent computations
3. Trace forward evaluation through a computational graph
4. Trace backward differentiation through the same graph
5. Understand why graphs enable automatic gradient computation

**Required Sections**:
1. **Expressions as Trees** — f(x,y) = x² + xy as a tree of operations
2. **Nodes and Edges**:
   - Leaf nodes: inputs and constants
   - Internal nodes: operations (+, ×, sin, etc.)
   - Edges: data flow
3. **Forward Mode** — Evaluate from leaves to root
4. **The Gradient Problem** — How to get derivatives automatically?
5. **Backward Mode (Reverse Mode Autodiff)**:
   - Start at root with gradient = 1
   - Propagate gradients backward using local rules
   - Each node type has a backward rule
6. **Local Gradient Rules**:
   - Addition: passes gradient unchanged to both inputs
   - Multiplication: gradient × other input
   - Power: gradient × n × x^(n-1)
7. **Why Graphs Enable Autodiff**:
   - Every computation recorded
   - Backward pass follows recorded path
   - PyTorch/TensorFlow build these graphs automatically
8. **Dynamic vs Static Graphs** — PyTorch (dynamic) vs old TensorFlow (static)
9. **Why This Matters for ML/AI**:
   - Neural networks ARE computational graphs
   - Autodiff = automatic backprop
   - Understanding graphs helps debug gradient issues

**Tone**: Build from simple expressions to complex ones. Emphasize the "automatic" nature.

**Length**: Approximately 1800-2200 words with multiple graph examples.
```
