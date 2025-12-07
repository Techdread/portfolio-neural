# D4: Regularisation Visualised — Three.js Visualization Prompt

## Visualization ID
D4

## Title
Regularisation Visualised

## Description
L1 diamond vs L2 circle constraints. Why L1 promotes sparsity.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: D4
**Title**: Regularisation Visualised
**Description**: L1 diamond vs L2 circle constraints. Why L1 promotes sparsity.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands loss functions and optimization

**Learning Objectives the visualization must support**:
1. See L2 constraint as circle, L1 as diamond
2. Watch loss contours expand to meet constraint
3. See L1 hitting corners (sparse solutions)
4. See L2 touching smooth boundary (dense solutions)
5. Understand regularisation strength effect

**Required Interactive Features**:

**2D Parameter Space**:
1. **Two Weights**: w₁ on x-axis, w₂ on y-axis
2. **Loss Contours**: Elliptical contours of unregularised loss
3. **Constraint Region**:
   - L2: Circle ||w||² ≤ c
   - L1: Diamond ||w||₁ ≤ c
   - Toggle between them
4. **Optimal Point**: Where contour meets constraint

**Constraint Visualization**:
1. **Regularisation Toggle**: L1 / L2 / Both
2. **Strength Slider (λ)**: Adjusts constraint size
3. **Animation**: Watch constraint shrink as λ increases
4. **Optimal Point Movement**: See solution move with λ

**Sparsity Demonstration**:
1. **L1 Focus**: Show corner-hitting behavior
2. **Rotate Loss Contours**: Different loss orientations
3. **Corner Preference**: Highlight how often L1 hits corners
4. **L2 Comparison**: Same loss orientation, different solution

**Side-by-Side View**:
1. **L1 Panel**: Diamond constraint with optimal point
2. **L2 Panel**: Circle constraint with optimal point
3. **Synchronized Contours**: Same loss in both
4. **Weight Value Display**: Show w₁, w₂ values for each

**Regularisation Path**:
1. **λ Sweep**: Animate λ from 0 to large
2. **Solution Path**: Trace how optimal point moves
3. **Sparsity Indicator**: Show when weights hit zero (L1)

**Interactive Loss**:
1. **Drag Loss Center**: Move optimal unregularised point
2. **Adjust Eccentricity**: Change loss contour shape
3. **See Effect**: Watch regularised solution change

**Visual Design Requirements**:
- Clear constraint boundaries (L1 diamond, L2 circle)
- Concentric loss contours with labels
- Highlighted optimal point with coordinate display
- Distinct colors for L1 vs L2 regions
- Animation showing constraint/contour interaction

**Code Architecture Requirements**:
- Loss contour computation
- Constraint boundary rendering
- Constrained optimization (find touching point)
- Animation for λ sweep
- Dual-view synchronization

**Deliverables**:
Complete TypeScript implementation with constraint visualization, sparsity demonstration, and regularisation path animation.
```
