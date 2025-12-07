# B3: The Gradient Vector — Three.js Visualization Prompt

## Visualization ID
B3

## Title
The Gradient Vector

## Description
Arrow pointing uphill on 2D surface in 3D view. Show why negative gradient = steepest descent.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: B3
**Title**: The Gradient Vector
**Description**: Arrow pointing uphill on 2D surface in 3D view. Show why negative gradient = steepest descent.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands partial derivatives (B2)
- User understands vectors (A1)

**Learning Objectives the visualization must support**:
1. See the gradient as an arrow in the xy-plane
2. Understand the gradient points toward steepest ascent
3. See negative gradient pointing downhill
4. Watch gradient-based movement minimize function

**Required Interactive Features**:

**3D Surface View**:
1. **Surface Rendering**: Same setup as B2, height-colored surface
2. **Function Options**: Bowl (x²+y²), saddle (x²-y²), wavy surface, custom
3. **Orbit Controls**: Full 3D navigation

**Gradient Visualization**:
1. **Current Point**: Draggable point on surface
2. **Gradient Arrow**: Arrow in xy-plane at the point's (x,y) position
   - Arrow direction: gradient direction
   - Arrow length: gradient magnitude
   - Color: green (positive gradient)
3. **Negative Gradient Arrow**: Optional toggle
   - Opposite direction
   - Color: red (descent direction)
4. **Partial Derivative Arrows**: Show ∂f/∂x and ∂f/∂y components separately

**Steepest Ascent/Descent Demo**:
1. **Step Uphill Button**: Move point in gradient direction
2. **Step Downhill Button**: Move point in negative gradient direction
3. **Animate Descent**: Auto-run gradient descent with small step size
4. **Learning Rate Slider**: Control step size
5. **Path Trail**: Show history of visited points

**Top-Down View**:
1. **2D Projection**: Looking down at xy-plane
2. **Contour Lines**: Show level curves of the function
3. **Gradient Arrows**: Show gradients perpendicular to contours
4. **Gradient Field**: Grid of small arrows showing gradient at multiple points

**Visual Design Requirements**:
- Surface with gradient coloring (cool = low, warm = high)
- Thick, clearly visible gradient arrows
- Trail as connected line with point markers
- Contour lines as curves in top-down view
- Split-screen option: 3D view + top-down view

**Code Architecture Requirements**:
- Numerical gradient computation
- Path history management
- Contour line generation
- Multiple view synchronization
- Animation loop for descent

**Deliverables**:
Complete TypeScript implementation with 3D surface, gradient arrows, descent animation, and contour view.
```
