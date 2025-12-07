# B1: Derivative as Slope — Three.js Visualization Prompt

## Visualization ID
B1

## Title
Derivative as Slope

## Description
Interactive function with draggable point showing tangent line. Visualize limit definition.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: B1
**Title**: Derivative as Slope
**Description**: Interactive function with draggable point showing tangent line. Visualize limit definition.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic graphing
- Knows what slope means for straight lines

**Learning Objectives the visualization must support**:
1. See the tangent line as "slope at a point"
2. Watch secant line become tangent as points converge
3. See derivative value change as point moves along curve
4. Understand positive/negative/zero derivative visually

**Required Interactive Features**:

**Main View**:
1. **Function Curve**: Smooth curve drawn on 2D plane
2. **Function Selector**: Dropdown with options:
   - y = x² (parabola)
   - y = x³ (cubic)
   - y = sin(x)
   - y = e^x
   - Custom function input
3. **Draggable Point**: Point on curve that user can drag along it
4. **Tangent Line**: Line tangent to curve at current point
5. **Derivative Value Display**: Show f'(x) = [value] in real-time

**Limit Definition Mode**:
1. **Second Point**: Movable point h units away from main point
2. **Secant Line**: Line connecting the two points
3. **h Slider**: Drag to change distance between points (0.001 to 2)
4. **Convergence Animation**: Button to animate h → 0
5. **Slope Display**: Show secant slope approaching derivative value
6. **Visual Formula**: Show [f(x+h) - f(x)] / h with current values

**Additional Features**:
1. **Derivative Sign Indicator**:
   - Green tangent line when f'(x) > 0 (increasing)
   - Red when f'(x) < 0 (decreasing)
   - Yellow when f'(x) ≈ 0 (local extremum)
2. **Derivative Function Plot**: Option to show f'(x) curve below main curve
3. **Critical Points Marker**: Highlight where f'(x) = 0

**Visual Design Requirements**:
- Clean 2D coordinate system with grid
- Smooth curve rendering (many line segments or bezier)
- Tangent line extends beyond point for visibility
- Point highlight with coordinate tooltip
- Animated transitions when changing functions

**Code Architecture Requirements**:
- Function evaluator supporting standard math functions
- Numerical derivative computation
- Line-curve intersection calculations
- Smooth dragging interaction along curve
- Responsive canvas sizing

**Deliverables**:
Complete TypeScript implementation with main view and limit mode, smooth interactions, and clear derivative display.
```
