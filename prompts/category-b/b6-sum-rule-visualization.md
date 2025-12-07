# B6: Sum Rule & Linearity — Three.js Visualization Prompt

## Visualization ID
B6

## Title
Sum Rule & Linearity

## Description
Derivatives distributing over addition. Simple but foundational.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: B6
**Title**: Sum Rule & Linearity
**Description**: Derivatives distributing over addition. Simple but foundational.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic derivatives (B1)

**Learning Objectives the visualization must support**:
1. See two functions adding to form a third
2. Watch derivatives add correspondingly
3. Understand scaling a function scales its derivative
4. See linearity in action

**Required Interactive Features**:

**Function Addition View**:
1. **Three Plots**:
   - Plot 1: f(x)
   - Plot 2: g(x)
   - Plot 3: h(x) = f(x) + g(x) (highlighted as result)
2. **Function Selectors**: Choose f and g from presets
3. **Vertical Stacking Visual**: Show f(x) + g(x) as stacked heights
4. **Draggable Point**: Move x value, see all three curves update

**Derivative Visualization**:
1. **Tangent Lines**: Show tangent on each curve at current x
2. **Slope Values**: Display f'(x), g'(x), h'(x)
3. **Sum Verification**: Show f'(x) + g'(x) = h'(x) numerically
4. **Derivative Curves**: Option to plot f', g', h' as separate curves

**Constant Multiple View**:
1. **Single Function f(x)**: With slider
2. **Constant Slider c**: From -3 to 3
3. **Scaled Function cf(x)**: Show stretched/flipped version
4. **Derivative Comparison**: Show (cf)' = c·f' visually

**Linearity Demo**:
1. **Linear Combination**: h(x) = a·f(x) + b·g(x)
2. **a and b Sliders**: Adjust coefficients
3. **Derivative Display**: Show h'(x) = a·f'(x) + b·g'(x)
4. **Interactive Verification**: Adjust a, b, watch relationship hold

**Visual Design Requirements**:
- Clear multi-plot layout (stacked or side-by-side)
- Consistent colors: f in blue, g in green, sum in purple
- Tangent lines clearly visible on each curve
- Numeric displays prominent and updating live
- Visual "=" signs connecting slope values

**Code Architecture Requirements**:
- Multi-function plotter
- Synchronized x-position across plots
- Derivative computation for arbitrary functions
- Responsive layout for multiple panels

**Deliverables**:
Complete TypeScript implementation with function addition view, derivative visualization, and linearity demonstration.
```
