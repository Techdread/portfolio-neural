# F3: Weight Initialisation Comparison — Three.js Visualization Prompt

## Visualization ID
F3

## Title
Weight Initialisation Comparison

## Description
Xavier, He, random — activation distributions through layers over epochs.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: F3
**Title**: Weight Initialisation Comparison
**Description**: Xavier, He, random — activation distributions through layers over epochs.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands activations and gradient flow

**Learning Objectives the visualization must support**:
1. See how different initializations affect activations
2. Watch activation distributions evolve during training
3. Compare stable vs unstable distributions
4. Understand Xavier vs He vs random

**Required Interactive Features**:

**Network View**:
1. **Multi-Layer Network**: 5-8 layer visualization
2. **Layer Blocks**: Each layer represented
3. **Activation Histograms**: Distribution at each layer
4. **Connection Lines**: Showing data flow

**Initialization Selector**:
1. **Random (Naive)**: Uniform or normal without scaling
2. **Xavier/Glorot**: Properly scaled for tanh/sigmoid
3. **He/Kaiming**: Properly scaled for ReLU
4. **Custom**: Manual variance input
5. **Apply Button**: Reinitialize network

**Comparison Mode**:
1. **Side-by-Side**: Two networks with different initializations
2. **Same Input**: Feed identical data to both
3. **Synchronized Layers**: Aligned for comparison

**Activation Distribution Display**:
1. **Per-Layer Histograms**: Distribution of activations
2. **Animation Over Layers**: Watch distribution change as data passes through
3. **Variance Indicator**: Show variance shrinking or growing
4. **Saturation Warning**: Highlight when activations are all near 0 or 1

**Training Simulation**:
1. **Epoch Slider**: Jump to different training epochs
2. **Animate Training**: Watch distributions evolve over epochs
3. **Gradient Magnitudes**: Show gradient health alongside
4. **Loss Curve**: Track training progress

**Activation Function Integration**:
1. **Activation Selector**: ReLU, Sigmoid, Tanh
2. **Initialization Recommendation**: Highlight best init for chosen activation
3. **Show Mismatch**: Demo Xavier with ReLU (suboptimal)

**Statistics Panel**:
1. **Layer-by-Layer Variance**: Numeric values
2. **Dead Neuron Count**: For ReLU (neurons stuck at 0)
3. **Saturation Percentage**: For sigmoid/tanh

**Visual Design Requirements**:
- Clean histogram visualization
- Color gradient for healthy/unhealthy distributions
- Clear layer labels
- Smooth animation for training evolution
- Side-by-side comparison layout

**Code Architecture Requirements**:
- Initialization function implementations
- Forward pass simulation
- Histogram computation
- Training loop simulation
- Multi-network state management

**Deliverables**:
Complete TypeScript implementation with initialization options, distribution visualization, training simulation, and comparison mode.
```
