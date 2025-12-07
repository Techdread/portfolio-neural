# A6: Basis Vectors & Change of Basis — Three.js Visualization Prompt

## Visualization ID
A6

## Title
Basis Vectors & Change of Basis

## Description
Same point in different coordinate systems. Foundation for embedding spaces.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A6
**Title**: Basis Vectors & Change of Basis
**Description**: Same point in different coordinate systems. Foundation for embedding spaces.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands vectors and matrix operations

**Learning Objectives the visualization must support**:
1. See basis vectors as coordinate system defining arrows
2. Watch grid transform when basis changes
3. See same point with different coordinate values
4. Understand change of basis as matrix operation

**Required Interactive Features**:

**Dual View Mode**:
1. **Side-by-Side Canvases**:
   - Left: Standard basis (i = [1,0], j = [0,1])
   - Right: Custom basis
2. **Linked Point**: Same geometric point shown in both, with different coordinates displayed
3. **Draggable Point**: Move point, watch coordinates update in both views

**Basis Editor**:
1. **Draggable Basis Vectors**: Click and drag to modify custom basis
2. **Numeric Input**: Direct entry of basis vector components
3. **Preset Bases**:
   - Standard basis
   - Rotated basis (45°)
   - Scaled basis
   - Skewed basis
4. **Grid Visualization**: Grid lines aligned with basis vectors

**Transformation View**:
1. **Change of Basis Matrix**: Display the matrix that converts coordinates
2. **Animate Conversion**: Show coordinates transforming through matrix multiplication
3. **Inverse Matrix**: Show conversion back to standard basis

**Embedding Analogy Section** (bonus):
1. **Word Example**: Show how "king" might have coordinates in embedding space
2. **Different Bases = Different Features**: Visualize re-projecting to different meaningful axes

**Visual Design Requirements**:
- Clear, labeled basis vectors (e.g., b₁, b₂ or custom labels)
- Grid that morphs with basis
- Point with coordinate readout in both systems
- Smooth animation when basis changes
- Different colors for each coordinate system's grid

**Code Architecture Requirements**:
- Basis class with transformation methods
- Synchronized dual canvas rendering
- Coordinate conversion utilities
- Animation interpolation for smooth basis transitions

**Deliverables**:
Complete TypeScript implementation with dual-view display, draggable elements, and clear coordinate readouts.
```
