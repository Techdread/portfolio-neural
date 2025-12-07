# A5: Eigenvalues & Eigenvectors — Three.js Visualization Prompt

## Visualization ID
A5

## Title
Eigenvalues & Eigenvectors Visualizer

## Description
Vectors that only scale under transformation. Link to PCA for dimensionality reduction.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A5
**Title**: Eigenvalues & Eigenvectors Visualizer
**Description**: Vectors that only scale under transformation. Link to PCA for dimensionality reduction.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands matrix transformations

**Learning Objectives the visualization must support**:
1. See that most vectors rotate AND scale under transformation
2. See eigenvectors only scale (stay on same line)
3. Understand eigenvalue as the scaling factor
4. Connect to PCA (bonus view)

**Required Interactive Features**:

**Main Exploration View**:
1. **Matrix Input**: Editable 2×2 matrix
2. **Matrix Presets**:
   - Scaling (diagonal) — easy eigenvectors
   - Rotation — no real eigenvectors
   - Shear — one eigenvector
   - Symmetric — orthogonal eigenvectors
3. **Vector Field Display**: Grid of vectors before/after transformation
4. **Highlight Eigenvectors**: Special color for eigenvector directions
5. **Interactive Vector**: Drag a vector, see its transformation
   - Changes color when aligned with eigenvector direction
   - Shows "only scaling!" indicator when on eigenvector

**Eigenspace View**:
1. **Eigenvector Arrows**: Display computed eigenvectors
2. **Eigenvalue Labels**: Show λ₁, λ₂ values
3. **Animation**: Apply matrix repeatedly, show eigenvectors are stable directions
4. **Scaling Indicator**: Visual showing stretch/compress amount

**PCA Connection View** (bonus):
1. **Data Cloud**: 2D scatter plot of data points
2. **Covariance Ellipse**: Show data spread
3. **Principal Components**: Eigenvectors of covariance as arrows
4. **Projection Demo**: Project data onto PC1, show variance preserved

**Visual Design Requirements**:
- Vector field with consistent base positions
- Clear before/after states (ghost vs solid)
- Eigenvector directions as dashed infinite lines through origin
- Eigenvalue magnitude shown by arrow thickness or glow
- Color coding: λ > 0 (one color), λ < 0 (another color)

**Code Architecture Requirements**:
- Numeric eigenvector computation (power iteration or analytic for 2×2)
- Vector field renderer
- Smooth transformation animations
- Clear separation between math computation and rendering

**Deliverables**:
Complete TypeScript implementation with eigenvector highlighting, interactive exploration, and optional PCA view.
```
