# D2: Learning Rate Effects — Three.js Visualization Prompt

## Visualization ID
D2

## Title
Learning Rate Effects

## Description
Interactive slider showing too small, just right, too large learning rates with real-time descent path.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: D2
**Title**: Learning Rate Effects
**Description**: Interactive slider showing too small, just right, too large learning rates with real-time descent path.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands gradient descent basics

**Learning Objectives the visualization must support**:
1. See slow convergence with small learning rate
2. See smooth convergence with good learning rate
3. See divergence with large learning rate
4. Understand the goldilocks zone

**Required Interactive Features**:

**Main Visualization**:
1. **2D Contour Surface**: Simple convex loss function
2. **Descent Path**: Trail showing optimization trajectory
3. **Current Position Marker**: Ball at current position
4. **Optimal Point**: Marker at minimum

**Learning Rate Control**:
1. **Interactive Slider**: Range from 0.001 to 2.0 (log scale)
2. **Preset Buttons**:
   - Too Small (e.g., 0.001)
   - Good (e.g., 0.1)
   - Too Large (e.g., 1.5)
3. **Current Value Display**: Show exact learning rate

**Real-Time Descent**:
1. **Auto-Run**: Continuously step while playing
2. **Real-Time Update**: Change learning rate mid-descent
3. **Instant Feedback**: See effect immediately

**Diagnostic Displays**:
1. **Loss Curve**: Plot loss vs iteration
2. **Step Size Indicator**: Show actual step magnitude
3. **Convergence Status**:
   - "Converging slowly" (small LR)
   - "Converging well" (good LR)
   - "Oscillating" (large LR)
   - "DIVERGING" (too large)
4. **Warning Indicators**: Visual alert when diverging

**Learning Rate Finder Mode**:
1. **Sweep Button**: Automatically sweep learning rates
2. **Loss vs LR Plot**: Classic finder plot
3. **Suggested Range**: Highlight good learning rate region

**Schedule Demo** (optional):
1. **Schedule Selector**: Step, exponential, cosine
2. **Schedule Visualization**: Plot LR over time
3. **Apply Schedule**: Run descent with schedule

**Visual Design Requirements**:
- Smooth contour lines on loss surface
- Path trail with gradient coloring (older = faded)
- Clear "danger zone" indication when LR too high
- Loss curve with clear axis labels
- Prominent learning rate display

**Code Architecture Requirements**:
- Gradient descent loop with configurable LR
- Real-time path rendering
- Loss history tracking
- Learning rate schedule functions
- Diagnostic computation (is diverging, etc.)

**Deliverables**:
Complete TypeScript implementation with interactive slider, real-time descent, diagnostic displays, and learning rate finder.
```
