# C5: Loss Function Landscapes — Three.js Visualization Prompt

## Visualization ID
C5

## Title
Loss Function Landscapes

## Description
Compare MSE, cross-entropy, hinge loss surfaces and optimization behavior.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C5
**Title**: Loss Function Landscapes
**Description**: Compare MSE, cross-entropy, hinge loss surfaces and optimization behavior.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands optimization basics

**Learning Objectives the visualization must support**:
1. See different loss function shapes
2. Compare how loss responds to predictions
3. Watch optimization behave differently on each
4. Understand gradient magnitude differences

**Required Interactive Features**:

**1D Loss View** (prediction vs loss):
1. **Single Prediction Slider**: Move predicted value
2. **True Value Marker**: Fixed target value
3. **Loss Curves**: Plot all loss functions vs prediction
4. **Current Loss Point**: Marker showing loss at current prediction
5. **Gradient Arrow**: Show direction and magnitude of gradient

**2D Loss Surface** (two parameters):
1. **Surface Selector**: Choose which loss to display as 3D surface
2. **Parameter Axes**: Two weights/parameters on x-y plane
3. **Loss Height**: Z-axis as loss value
4. **Gradient Descent Path**: Watch optimizer traverse surface
5. **Comparison Mode**: Side-by-side surfaces for different losses

**Classification Focus**:
1. **Binary Classification Setup**: True class (0 or 1), predicted probability
2. **Cross-Entropy Plot**: Asymmetric curve showing harsh penalty
3. **Confidence Slider**: See how confident wrong predictions are penalized
4. **Comparison to MSE**: Overlay showing different gradients

**Multi-Parameter Landscape**:
1. **Simple Network**: 2-weight network for visualization
2. **Data Points**: Small dataset determining the loss surface
3. **Animate Training**: Watch weights move on loss surface
4. **Switch Loss Function**: See path change with different losses

**Visual Design Requirements**:
- 3D surfaces with height-based coloring
- Gradient vectors as arrows
- Training path as connected line with markers
- Side-by-side comparison layout
- Clear loss value displays

**Code Architecture Requirements**:
- Loss function classes (forward and gradient methods)
- Surface mesh generation from loss function
- Optimizer simulation
- Multiple synchronized views
- Comparison rendering system

**Deliverables**:
Complete TypeScript implementation with loss curves, 3D surfaces, gradient visualization, and training simulation.
```
