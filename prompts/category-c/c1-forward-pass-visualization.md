# C1: Forward Pass Step-by-Step — Three.js Visualization Prompt

## Visualization ID
C1

## Title
Forward Pass Step-by-Step

## Description
Data flowing through layers: input → weighted sum → activation → output. Show actual numbers.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C1
**Title**: Forward Pass Step-by-Step
**Description**: Data flowing through layers: input → weighted sum → activation → output. Show actual numbers.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands vectors, dot products, matrices

**Learning Objectives the visualization must support**:
1. See neurons as processing units receiving and sending values
2. Watch data flow step-by-step through the network
3. See exact numbers at every stage
4. Understand the sequence: input → weighted sum → bias → activation → output

**Required Interactive Features**:

**Network Structure**:
1. **Configurable Architecture**:
   - Default: 2 inputs → 3 hidden → 2 outputs
   - Adjustable layer count (1-4 layers)
   - Adjustable neurons per layer
2. **Neuron Display**: Circles/nodes representing neurons
3. **Connection Lines**: Lines between neurons showing weights
4. **Weight Labels**: Show weight value on each connection

**Input Controls**:
1. **Input Sliders**: Set each input value (-1 to 1)
2. **Preset Inputs**: Quick buttons for common test values
3. **Random Inputs**: Generate random input values

**Weight/Bias Controls**:
1. **Editable Weights**: Click to modify any weight
2. **Random Weights**: Initialize randomly
3. **Preset Networks**: Load pre-configured networks that demonstrate specific behaviors

**Step-by-Step Animation**:
1. **Full Auto Play**: Run entire forward pass with animation
2. **Step Forward Button**: Advance one computation at a time
3. **Step Back Button**: Go back to see previous state
4. **Speed Control**: Slow/medium/fast animation
5. **Current Step Indicator**: "Computing weighted sum for hidden neuron 2"

**Value Displays**:
1. **Neuron Values**: Show current value inside or beside each neuron
2. **Weighted Sum Breakdown**: On hover, show w₁x₁ + w₂x₂ + ... + b = sum
3. **Pre-Activation vs Post-Activation**: Show value before and after activation
4. **Formula Panel**: Display the formula being computed at current step

**Activation Function**:
1. **Function Selector**: ReLU, Sigmoid, Tanh, Linear
2. **Mini Graph**: Small plot of activation function beside each layer

**Visual Design Requirements**:
- Layered left-to-right layout (input → hidden → output)
- Animated "pulse" traveling along connections
- Color intensity on neurons based on activation value
- Positive weights in one color, negative in another
- Clear layer separation with labels

**Code Architecture Requirements**:
- Network class with configurable architecture
- Forward pass function with step-by-step mode
- Animation timeline system
- State management for replay/rewind
- Modular neuron and layer components

**Deliverables**:
Complete TypeScript implementation with full animation system, editable parameters, and clear numeric displays at every step.
```
