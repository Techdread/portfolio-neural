# G1: Perceptron Playground — Three.js Visualization Prompt

## Visualization ID
G1

## Title
Perceptron Playground

## Description
Drag points, watch perceptron find separating hyperplane. Show linear limits.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: G1
**Title**: Perceptron Playground
**Description**: Drag points, watch perceptron find separating hyperplane. Show linear limits.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic 2D coordinates

**Learning Objectives the visualization must support**:
1. Create datasets by placing points
2. Watch perceptron learn to separate classes
3. See the decision boundary update
4. Discover XOR limitation interactively

**Required Interactive Features**:

**Data Canvas**:
1. **2D Plane**: Coordinate grid for placing points
2. **Add Points**: Click to place points
3. **Class Selection**: Toggle between class A (blue) and class B (red)
4. **Drag Points**: Move existing points to new positions
5. **Delete Points**: Right-click or button to remove
6. **Clear All**: Reset canvas

**Perceptron Visualization**:
1. **Decision Boundary Line**: Shows current w·x + b = 0
2. **Boundary Animation**: Smooth updates as weights change
3. **Positive/Negative Regions**: Background shading for each class
4. **Weight Vector Arrow**: Optional display of w vector

**Training Controls**:
1. **Train Button**: Run perceptron algorithm
2. **Step Mode**: One update at a time
3. **Speed Control**: Fast/slow training animation
4. **Current Step Display**: "Training: epoch 3, point 5"
5. **Reset Weights**: Reinitialize randomly

**Learning Visualization**:
1. **Current Point Highlight**: Show which point is being checked
2. **Correct/Wrong Indicator**: Green/red flash on classification
3. **Weight Update Animation**: Show weight vector shifting
4. **Convergence Indicator**: "Converged!" when all correct

**Preset Datasets**:
1. **Linearly Separable**: Easy dataset
2. **XOR Pattern**: Four points in XOR configuration
3. **Almost Separable**: One outlier
4. **Random Clusters**: Random linearly separable data

**XOR Demonstration**:
1. **XOR Preset Button**: Load XOR points automatically
2. **Failure Mode**: Watch perceptron oscillate without converging
3. **Iteration Counter**: Show it trying forever
4. **Explanation Popup**: Why this fails

**Neuron Diagram** (side panel):
1. **Visual Neuron**: Inputs, weights, sum, activation
2. **Current Values**: Live weight and bias values
3. **Output**: Current classification

**Visual Design Requirements**:
- Clean grid background
- Distinct class colors (blue/red)
- Smooth line animation
- Point selection highlight
- Clear region coloring

**Code Architecture Requirements**:
- Perceptron class with update method
- Point management (add, remove, drag)
- Decision boundary calculation
- Step-by-step training mode
- Convergence detection

**Deliverables**:
Complete TypeScript implementation with point manipulation, perceptron training, XOR demo, and visual neuron diagram.
```
