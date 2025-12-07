# F1: Loss Landscape Terrain — Three.js Visualization Prompt

## Visualization ID
F1

## Title
Loss Landscape Terrain

## Description
Loss surface as 3D terrain, gradient descent as ball rolling downhill.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: F1
**Title**: Loss Landscape Terrain
**Description**: Loss surface as 3D terrain, gradient descent as ball rolling downhill.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands loss functions and gradient descent

**Learning Objectives the visualization must support**:
1. See loss landscape as terrain
2. Watch ball roll downhill following gradients
3. Identify local minima, global minima, saddle points
4. Understand optimization challenges visually

**Required Interactive Features**:

**3D Terrain View**:
1. **Height-Mapped Surface**: Loss function as 3D mesh
2. **Surface Presets**:
   - Convex bowl (easy optimization)
   - Multiple minima (local vs global)
   - Saddle point surface
   - Ridge/ravine (elongated valley)
   - Complex landscape (multiple features)
3. **Terrain Texture**: Height-based coloring (blue=low, red=high)
4. **Camera Controls**: Orbit, pan, zoom

**Ball Physics**:
1. **Ball Object**: Sphere representing current position
2. **Rolling Animation**: Ball follows gradient
3. **Momentum Effect**: Ball continues rolling, can overshoot
4. **Trail**: Path traced by ball

**Interactive Controls**:
1. **Drop Ball**: Click on surface to place ball
2. **Release/Start**: Begin gradient descent
3. **Pause/Resume**: Stop ball mid-descent
4. **Reset**: Return to initial state

**Optimizer Selection**:
1. **Vanilla GD**: Basic gradient following
2. **Momentum**: Ball gains speed
3. **Adam**: Adaptive behavior
4. **Compare Mode**: Multiple balls with different optimizers

**Learning Rate Control**:
1. **Slider**: Adjust step size
2. **Real-Time Effect**: See ball behavior change
3. **Divergence Demo**: High LR makes ball fly off

**Critical Point Markers**:
1. **Minima Flags**: Mark local and global minima
2. **Saddle Point Marker**: Special indicator for saddle points
3. **Hover Info**: Show point type and loss value

**2D Slice View** (supplementary):
1. **Cross-Section**: Cut through 3D surface
2. **Ball Position**: Project ball onto slice
3. **Gradient Arrow**: Show descent direction

**Visual Design Requirements**:
- Realistic terrain appearance
- Smooth rolling animation
- Clear height coloring
- Ball shadow on surface
- Visible gradient direction at ball

**Code Architecture Requirements**:
- Surface mesh generation from loss function
- Physics simulation (simplified gravity/gradient)
- Multiple optimizer implementations
- Camera and controls setup
- Trail rendering

**Deliverables**:
Complete TypeScript implementation with terrain visualization, ball physics, optimizer comparison, and interactive placement.
```
