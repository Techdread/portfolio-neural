# F2: Backprop Gradient Flow — Three.js Visualization Prompt

## Visualization ID
F2

## Title
Backprop Gradient Flow

## Description
Gradients flowing backwards, color-coded by magnitude. Show vanishing/exploding.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: F2
**Title**: Backprop Gradient Flow
**Description**: Gradients flowing backwards, color-coded by magnitude. Show vanishing/exploding.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands backpropagation basics

**Learning Objectives the visualization must support**:
1. See gradients flow backward layer by layer
2. Watch gradient magnitude change through network
3. Observe vanishing gradient (fading)
4. Observe exploding gradient (brightening)

**Required Interactive Features**:

**Network Display**:
1. **Deep Network Architecture**: 5-10 layers configurable
2. **Layer Blocks**: Visual representation of each layer
3. **Connection Lines**: Between layers
4. **Neuron Representation**: Simplified or detailed view

**Gradient Flow Animation**:
1. **Backward Flow**: Gradient pulses traveling from output to input
2. **Color Coding**: 
   - Bright = large gradient
   - Dim = small gradient
   - Red alert = exploding (too large)
3. **Magnitude Labels**: Numeric values at each layer
4. **Flow Speed**: Adjustable animation speed

**Configuration Panel**:
1. **Activation Selector**: Sigmoid, Tanh, ReLU, Leaky ReLU
2. **Layer Count**: Adjust depth (2 to 15 layers)
3. **Weight Initialization**: Random, Xavier, He
4. **Initial Gradient**: Set starting gradient magnitude

**Vanishing Demo**:
1. **Preset: Sigmoid Deep Network**: 10+ layers with sigmoid
2. **Watch Gradient Fade**: Color dims toward early layers
3. **Gradient Chart**: Bar chart of gradient magnitude per layer

**Exploding Demo**:
1. **Preset: Bad Initialization**: Large weights, deep network
2. **Watch Gradient Grow**: Color intensifies backward
3. **NaN Warning**: Alert when gradient explodes

**Solution Comparisons**:
1. **Toggle ReLU**: Switch activation, see improved flow
2. **Add Skip Connection**: Show residual path with preserved gradient
3. **Add Batch Norm**: Show normalized gradient flow
4. **Gradient Clipping**: Cap exploding gradients

**Histogram View**:
1. **Gradient Distribution**: Histogram of gradient values
2. **Per-Layer Histograms**: Side-by-side comparison
3. **Healthy vs Unhealthy**: Reference for good distribution

**Visual Design Requirements**:
- Gradient magnitude as color intensity + glow
- Clear layer separation
- Animated flow from right to left
- Warning indicators for problematic gradients
- Clean chart displays

**Code Architecture Requirements**:
- Network simulation with forward/backward pass
- Gradient computation per layer
- Animation sequencing
- Multiple preset configurations
- Real-time magnitude tracking

**Deliverables**:
Complete TypeScript implementation with gradient flow visualization, problem demos, and solution comparisons.
```
