# F4: Overfitting Visualised — Three.js Visualization Prompt

## Visualization ID
F4

## Title
Overfitting Visualised

## Description
Training vs validation loss diverging. Decision boundary becoming too complex.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: F4
**Title**: Overfitting Visualised
**Description**: Training vs validation loss diverging. Decision boundary becoming too complex.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable), TensorFlow.js (optional for real training)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands loss functions and training

**Learning Objectives the visualization must support**:
1. See training/validation loss curves diverge
2. Watch decision boundary evolve from simple to overfit
3. Identify the optimal stopping point
4. Understand regularization effect

**Required Interactive Features**:

**Data Display**:
1. **2D Scatter Plot**: Training data points (two classes)
2. **Validation Points**: Distinct markers for validation set
3. **Noise Level Slider**: Add noise to data
4. **Data Generation**: Create new random datasets

**Decision Boundary View**:
1. **Live Boundary**: Evolving as model trains
2. **Background Coloring**: Regions classified as each class
3. **Complexity Indicator**: Measure of boundary complexity
4. **Optimal vs Overfit Comparison**: Side-by-side

**Loss Curves**:
1. **Dual Lines**: Training loss and validation loss
2. **Real-Time Update**: Curves grow as training progresses
3. **Divergence Point Marker**: Highlight where gap opens
4. **Optimal Stop Point**: Mark best validation loss

**Training Controls**:
1. **Train Button**: Start/pause training
2. **Epoch Slider**: Jump to specific epoch
3. **Training Speed**: Fast/slow animation
4. **Reset**: Start over

**Model Complexity Control**:
1. **Hidden Layers Slider**: 1 to 5 layers
2. **Neurons per Layer**: Adjust model capacity
3. **See Effect**: Watch boundary complexity change

**Regularization Demos**:
1. **No Regularization**: Baseline overfit
2. **L2 Regularization Slider**: Add weight decay
3. **Dropout Slider**: Add dropout rate
4. **Early Stopping**: Auto-stop at best validation
5. **Compare Mode**: With vs without regularization

**Metrics Panel**:
1. **Train Accuracy**: Current training accuracy
2. **Validation Accuracy**: Current validation accuracy
3. **Gap Indicator**: Train - Validation difference
4. **Overfitting Alert**: Warning when gap is large

**Visual Design Requirements**:
- Clear scatter plot with class colors
- Smooth decision boundary rendering
- Loss curves with clear legend
- Highlighted divergence region
- Responsive layout for plots

**Code Architecture Requirements**:
- Simple neural network training loop
- Decision boundary computation
- Loss tracking and plotting
- Regularization implementations
- Dataset generation and splitting

**Deliverables**:
Complete TypeScript implementation with data visualization, training simulation, loss curves, and regularization comparison.
```
