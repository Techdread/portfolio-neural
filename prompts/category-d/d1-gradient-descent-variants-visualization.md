# D1: Gradient Descent Variants — Three.js Visualization Prompt

## Visualization ID
D1

## Title
Gradient Descent Variants

## Description
Compare vanilla, momentum, RMSprop, Adam on same surface. Show momentum escaping local minima.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: D1
**Title**: Gradient Descent Variants
**Description**: Compare vanilla, momentum, RMSprop, Adam on same surface. Show momentum escaping local minima.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands gradients and loss surfaces

**Learning Objectives the visualization must support**:
1. See how each optimizer behaves on the same surface
2. Watch momentum accumulate and overshoot
3. See adaptive learning rates in RMSprop/Adam
4. Compare convergence speeds

**Required Interactive Features**:

**Surface View**:
1. **3D Loss Surface**: Height-mapped terrain
2. **Surface Presets**:
   - Bowl (simple convex)
   - Ravine (elongated valley)
   - Local minima (multiple valleys)
   - Saddle point
3. **Top-Down View**: 2D contour plot option
4. **Surface Controls**: Orbit, zoom, pan

**Optimizer Comparison**:
1. **Simultaneous Runs**: All 4 optimizers start from same point
2. **Color-Coded Paths**:
   - Vanilla: Red
   - Momentum: Blue
   - RMSprop: Green
   - Adam: Orange
3. **Toggle Optimizers**: Show/hide each optimizer's path
4. **Starting Point**: Click to set starting position

**Animation Controls**:
1. **Play/Pause**: Start/stop optimization
2. **Step**: Single optimization step
3. **Speed Control**: Slow to fast animation
4. **Reset**: Return to starting positions
5. **Step Counter**: Show iteration number

**Parameter Controls**:
1. **Learning Rate**: Slider (0.001 to 1.0)
2. **Momentum β**: Slider for momentum coefficient
3. **RMSprop/Adam β₁, β₂**: Momentum decay parameters
4. **Apply to**: Select which optimizer to modify

**State Display**:
1. **Current Position**: (x, y, loss) for each optimizer
2. **Velocity Vectors**: Show momentum direction (for momentum/Adam)
3. **Effective Learning Rate**: Show adapted rate (for RMSprop/Adam)
4. **Convergence Status**: Indicate if optimizer has "converged"

**Escape Demo**:
1. **Local Minimum Trap**: Surface with shallow local minimum
2. **Watch Momentum Escape**: While vanilla gets stuck
3. **Highlighted Moment**: Call attention when escape happens

**Visual Design Requirements**:
- Distinct colors for each optimizer
- Path trails with point markers
- 3D surface with gradient coloring
- Current position markers (spheres)
- Legend for optimizer colors

**Code Architecture Requirements**:
- Optimizer classes with consistent interface
- State tracking (position, velocity, cache)
- Surface function evaluation
- Animation loop with step control
- Multiple path rendering

**Deliverables**:
Complete TypeScript implementation with simultaneous optimizer comparison, parameter controls, and escape demonstration.
```
