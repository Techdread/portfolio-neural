# A2: Matrix Multiplication — Three.js Visualization Prompt

## Visualization ID
A2

## Title
Matrix Multiplication Visualizer

## Description
Animate row-by-column multiplication step-by-step. Show matrices transforming space (rotation, scaling, shearing).

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A2
**Title**: Matrix Multiplication Visualizer
**Description**: Animate row-by-column multiplication step-by-step. Show matrices transforming space (rotation, scaling, shearing).

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User has completed A1 (Vector Operations)
- Understands vectors as arrows

**Learning Objectives the visualization must support**:
1. See how each output element is computed (row · column)
2. Understand dimension requirements for multiplication
3. Visualize matrices transforming 2D space
4. See why multiplication order changes the result

**Required Interactive Features**:

**Mode 1: Arithmetic View**
1. **Matrix Input**: Editable matrix cells (2×2, 2×3, 3×3 presets)
2. **Step-by-Step Animation**:
   - Highlight current row of matrix A
   - Highlight current column of matrix B
   - Animate dot product calculation
   - Fill in result cell with computed value
3. **Speed Control**: Slow/medium/fast animation
4. **Dimension Indicator**: Show (m×n) × (n×p) = (m×p)

**Mode 2: Transformation View**
1. **Grid of Points**: Unit square or shape made of points
2. **Matrix Selector**: Preset transformations (rotation, scale, shear, reflection)
3. **Custom Matrix**: Edit transformation matrix values
4. **Apply Animation**: Watch points smoothly transform
5. **Composition Demo**: Apply matrix A, then matrix B, show it equals AB applied once
6. **Order Toggle**: Compare AB vs BA transformations

**Visual Design Requirements**:
- Matrix cells clearly visible with grid lines
- Color coding: Row highlight, Column highlight, Result highlight
- Transformation view: before (ghost) and after positions
- Animated trails showing point movement
- Clear labels for matrix names (A, B, C = A×B)

**Code Architecture Requirements**:
- Separate modules for arithmetic view and transformation view
- Matrix class with multiplication method
- Animation timeline system for step control
- State management for current step in calculation
- TypeScript interfaces for Matrix types

**Deliverables**:
1. Complete TypeScript implementation
2. HTML/CSS for UI controls
3. Clear code comments explaining the math at each step
4. README with usage instructions

Provide complete, runnable code.
```
