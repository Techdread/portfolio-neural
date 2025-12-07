# A1: Vector Operations — Three.js Visualization Prompt

## Visualization ID
A1

## Title
Vector Operations Visualizer

## Description
Visualize vector addition, subtraction, scaling, and dot products in 2D/3D. Show dot product as similarity/angle measurement.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A1
**Title**: Vector Operations Visualizer
**Description**: Visualize vector addition, subtraction, scaling, and dot products in 2D/3D. Show dot product as similarity/angle measurement.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target
- Responsive: Desktop-first, but handle window resizing

**Prerequisites for this visualization**:
- User understands basic coordinate systems
- Part of a larger portfolio (consistent styling needed)

**Learning Objectives the visualization must support**:
1. See vectors as arrows with magnitude and direction
2. Watch vector addition happen step-by-step (tip-to-tail)
3. Observe scalar multiplication stretching/shrinking vectors
4. Understand dot product through angle visualization

**Required Interactive Features**:
1. **Mode Selector**: Toggle between 2D and 3D views
2. **Operation Tabs**: Addition, Subtraction, Scaling, Dot Product
3. **Draggable Vectors**: Click and drag to modify vector components
4. **Animation Controls**: Play/pause/step-through for operations
5. **Numeric Display**: Show vector components and results in real-time
6. **Dot Product Mode Specifics**:
   - Show angle between vectors with arc
   - Display cosine value
   - Color gradient indicating similarity (green = aligned, red = perpendicular/opposite)
7. **Grid & Axes**: Clear reference grid with labeled axes
8. **Reset Button**: Return to default vector positions

**Visual Design Requirements**:
- Clean, modern aesthetic (dark background recommended for contrast)
- Distinct colors for Vector A, Vector B, Result Vector
- Smooth animations (eased transitions, not instant)
- Labels on vectors showing their names and component values
- Subtle glow effects on vectors for visibility

**Code Architecture Requirements**:
- Modular structure (separate files for scene setup, vector rendering, UI controls)
- Clear TypeScript interfaces for Vector types
- Event-driven updates (state changes trigger re-renders)
- Well-commented code explaining mathematical operations
- Reusable components that could work for other linear algebra visualizations

**Deliverables**:
1. Main visualization TypeScript file
2. Supporting module files
3. HTML template with required containers
4. CSS for UI controls
5. README with setup instructions

Provide complete, runnable code with all imports and dependencies specified.
```
