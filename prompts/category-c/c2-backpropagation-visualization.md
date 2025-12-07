# C2: Backpropagation Walkthrough — Three.js Visualization Prompt

## Visualization ID
C2

## Title
Backpropagation Walkthrough

## Description
Error gradients flowing backwards. Chain rule at each node, accumulating gradients.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C2
**Title**: Backpropagation Walkthrough
**Description**: Error gradients flowing backwards. Chain rule at each node, accumulating gradients.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User has completed C1 (Forward Pass)
- User understands chain rule (B4)

**Learning Objectives the visualization must support**:
1. See gradients flowing backward through the network
2. Watch chain rule multiplication at each node
3. See gradients accumulate at weights
4. Understand the forward/backward pass relationship

**Required Interactive Features**:

**Network Display** (same as C1):
1. **Same Architecture Options**: Match C1 for continuity
2. **Forward Pass First**: Complete forward pass before backward
3. **Loss Computation**: Show loss value after forward pass

**Backward Pass Animation**:
1. **Step-by-Step Mode**: One gradient computation at a time
2. **Current Gradient Highlight**: Show which gradient is being computed
3. **Flow Animation**: Gradient "pulse" traveling backward on connections
4. **Multiplication Visualization**: Show chain rule multiplication at each node

**Gradient Displays**:
1. **Neuron Gradients**: ∂L/∂(neuron output) shown at each neuron
2. **Weight Gradients**: ∂L/∂w shown on each connection
3. **Local Derivative**: Show local derivative at each node (activation derivative, etc.)
4. **Multiplication Breakdown**: Show gradient_in × local_derivative = gradient_out

**Chain Rule Panel**:
1. **Current Computation**: Display the chain rule equation being computed
2. **Substituted Values**: Show numeric values plugged in
3. **Result**: Show computed gradient value

**Comparison View**:
1. **Side-by-Side**: Forward values on left, gradients on right
2. **Symmetry Highlighting**: Show correspondence between forward and backward paths
3. **Color Coding**: Gradient magnitude as color intensity

**Interactive Elements**:
1. **Target Value Input**: Set desired output (for loss computation)
2. **Loss Function Selector**: MSE, Cross-Entropy
3. **Gradient Check**: Numerical gradient approximation to verify

**Visual Design Requirements**:
- Reverse flow direction clearly indicated (arrows)
- Gradient values in different color than forward values
- Gradient magnitude as line thickness on connections
- Clear "backward pass" label/indicator
- Smooth animations with appropriate timing

**Code Architecture Requirements**:
- Backward pass function with step-by-step mode
- Gradient storage per weight and neuron
- Chain rule computation at each node
- Synchronization with forward pass state
- Clear data structures for gradient flow

**Deliverables**:
Complete TypeScript implementation that continues from C1's forward pass, with detailed backward pass animation and gradient display.
```
