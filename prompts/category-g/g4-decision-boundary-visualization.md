# G4: Decision Boundary Evolution — Three.js Visualization Prompt

## Visualization ID
G4

## Title
Decision Boundary Evolution

## Description
Watch classifier boundaries form during training on 2D data.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: G4
**Title**: Decision Boundary Evolution
**Description**: Watch classifier boundaries form during training on 2D data.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable), TensorFlow.js (for real training)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands classification and neural networks

**Learning Objectives the visualization must support**:
1. See decision boundary form from random start
2. Watch boundary evolve through training
3. Compare simple vs complex model boundaries
4. Identify underfitting and overfitting visually

**Required Interactive Features**:

**Data Canvas**:
1. **2D Scatter Plot**: Training points with class colors
2. **Add Points**: Click to add data
3. **Class Toggle**: Switch between classes when adding
4. **Preset Datasets**:
   - Linear separable
   - Circular/moon shapes
   - XOR pattern
   - Spiral
5. **Clear/Reset**: Remove all points

**Decision Boundary Visualization**:
1. **Background Coloring**: Regions colored by predicted class
2. **Boundary Line**: Explicit boundary contour
3. **Confidence Gradient**: Intensity based on classification confidence
4. **Real-Time Update**: Boundary updates during training

**Model Configuration**:
1. **Architecture Selector**:
   - Logistic regression (linear boundary)
   - 1 hidden layer (simple curves)
   - 2+ hidden layers (complex boundaries)
2. **Neurons per Layer**: Slider
3. **Activation Function**: ReLU, Tanh, Sigmoid

**Training Controls**:
1. **Train Button**: Start/pause training
2. **Epoch Counter**: Current iteration
3. **Step Mode**: One gradient update at a time
4. **Learning Rate Slider**: Adjust during training
5. **Reset Weights**: Reinitialize randomly

**Training Visualization**:
1. **Loss Curve**: Plot loss over epochs
2. **Accuracy Display**: Train/test accuracy
3. **Boundary History**: Ghost of past boundaries
4. **Animation Playback**: Replay training evolution

**Comparison Mode**:
1. **Side-by-Side**: Two models on same data
2. **Simple vs Complex**: Compare capacity effects
3. **Synchronized Training**: Both train simultaneously
4. **Metrics Comparison**: Loss/accuracy for both

**Overfitting Demo**:
1. **Complex Model Preset**: High-capacity network
2. **Watch Boundary Wiggles**: See overfitting develop
3. **Test Point Indicator**: Show generalization failure

**Visual Design Requirements**:
- Smooth boundary rendering (high resolution grid)
- Clear class colors (blue/red/orange)
- Confidence as color intensity
- Ghost boundaries for history
- Clean scatter point display

**Code Architecture Requirements**:
- TensorFlow.js model (configurable architecture)
- Dense grid prediction for boundary rendering
- Training loop with state capture
- History management for playback
- Multi-model comparison support

**Deliverables**:
Complete TypeScript implementation with data creation, real-time training visualization, model comparison, and overfitting demonstration.
```
