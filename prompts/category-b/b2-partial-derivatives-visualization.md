# B2: Partial Derivatives — Three.js Visualization Prompt

## Visualization ID
B2

## Title
Partial Derivatives Visualizer

## Description
3D surface with slices showing change along each axis independently.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: B2
**Title**: Partial Derivatives Visualizer
**Description**: 3D surface with slices showing change along each axis independently.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands single-variable derivatives (B1)

**Learning Objectives the visualization must support**:
1. See a function of two variables as a 3D surface
2. Understand slice curves (fixing one variable)
3. See partial derivative as slope of slice curve
4. Compare ∂f/∂x and ∂f/∂y at same point

**Required Interactive Features**:

**3D Surface View**:
1. **Surface Rendering**: Smooth 3D surface from f(x, y)
2. **Function Selector**:
   - f(x,y) = x² + y² (paraboloid)
   - f(x,y) = sin(x)cos(y) (wave)
   - f(x,y) = x² - y² (saddle)
   - f(x,y) = exp(-(x²+y²)) (Gaussian bump)
3. **Orbit Controls**: Rotate, zoom, pan the 3D view
4. **Grid on Surface**: Contour-like grid lines for depth perception

**Point Selection**:
1. **Draggable Point**: Point on surface user can move
2. **Point Projection**: Vertical line to xy-plane showing (x, y) position
3. **Coordinate Display**: Show (x, y, f(x,y)) values

**Slice Visualization**:
1. **X-Slice Toggle**: Show the slice curve where y = constant
   - Highlighted curve on surface
   - Tangent line showing ∂f/∂x slope
   - Display ∂f/∂x value
2. **Y-Slice Toggle**: Show the slice curve where x = constant
   - Highlighted curve on surface
   - Tangent line showing ∂f/∂y slope
   - Display ∂f/∂y value
3. **Both Slices Mode**: Show both slices simultaneously with different colors

**2D Slice Views** (optional split panel):
1. **X-Slice 2D Plot**: The slice curve in xz-plane with tangent
2. **Y-Slice 2D Plot**: The slice curve in yz-plane with tangent

**Visual Design Requirements**:
- Surface with gradient coloring based on height
- Transparent surface option to see internals
- Slice curves as thick colored lines (red for x-slice, blue for y-slice)
- Tangent lines as arrows
- Clear axis labels (x, y, f(x,y))

**Code Architecture Requirements**:
- Surface mesh generation from function
- Numerical partial derivative computation
- Slice curve extraction
- 3D camera and controls setup
- Efficient surface rendering (indexed geometry)

**Deliverables**:
Complete TypeScript implementation with interactive 3D surface, slice visualization, and partial derivative display.
```
