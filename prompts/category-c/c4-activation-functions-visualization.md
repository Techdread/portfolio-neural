# C4: Activation Functions Gallery — Three.js Visualization Prompt

## Visualization ID
C4

## Title
Activation Functions Gallery

## Description
Side-by-side comparison of sigmoid, tanh, ReLU, Leaky ReLU, GELU. Show function AND derivative.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C4
**Title**: Activation Functions Gallery
**Description**: Side-by-side comparison of sigmoid, tanh, ReLU, Leaky ReLU, GELU. Show function AND derivative.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands functions and derivatives

**Learning Objectives the visualization must support**:
1. Compare activation function shapes visually
2. See derivatives alongside the functions
3. Understand output ranges
4. Explore behavior at different input values
5. See the vanishing gradient problem visually

**Required Interactive Features**:

**Gallery View**:
1. **Grid Layout**: All activation functions in a grid (2-3 per row)
2. **Each Cell Contains**:
   - Function name and formula
   - Function plot
   - Derivative plot
   - Output range indicator
3. **Hover for Details**: Expanded info on hover

**Comparison Mode**:
1. **Overlay Plot**: Selected functions on same axes
2. **Function Toggle**: Checkboxes to show/hide each function
3. **Derivative Toggle**: Show derivatives instead of functions
4. **Normalized View**: Scale to compare shapes despite different ranges

**Interactive Point**:
1. **Draggable x-value**: Move along x-axis
2. **Value Display**: Show f(x) for each function at current x
3. **Derivative Display**: Show f'(x) for each function
4. **Comparison Table**: Numeric values in a table at current x

**Vanishing Gradient Demo**:
1. **Chain Multiplication**: Show what happens when gradient passes through many layers
2. **Layer Slider**: 1 to 50 layers
3. **Gradient Magnitude Plot**: Show gradient shrinking (sigmoid) vs stable (ReLU)
4. **Visual Alert**: Warning when gradient effectively vanishes

**Parameter Variants**:
1. **Leaky ReLU Slope**: Slider for negative slope (0.01 to 0.3)
2. **ELU Alpha**: Slider for alpha parameter
3. **Softplus Beta**: Temperature parameter

**Visual Design Requirements**:
- Consistent color per function across all views
- Clear axis labels and grid lines
- Function formula displayed in LaTeX-style rendering
- Smooth curves with many sample points
- Responsive grid layout

**Code Architecture Requirements**:
- Activation function classes with forward() and derivative() methods
- Configurable plot component
- Comparison overlay renderer
- Gradient chain computation
- Parameter binding for variants

**Deliverables**:
Complete TypeScript implementation with gallery view, comparison mode, interactive exploration, and vanishing gradient demonstration.
```
