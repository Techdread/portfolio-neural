# B5: Product Rule — Three.js Visualization Prompt

## Visualization ID
B5

## Title
Product Rule Visualizer

## Description
Area of rectangle: d(uv) = u·dv + v·du. Animate both terms contributing.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: B5
**Title**: Product Rule Visualizer
**Description**: Area of rectangle: d(uv) = u·dv + v·du. Animate both terms contributing.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic derivatives (B1)

**Learning Objectives the visualization must support**:
1. See the product of two functions as rectangle area
2. Watch area change decompose into two terms
3. Understand why (fg)' = f'g + fg'
4. See the "small corner" term that vanishes

**Required Interactive Features**:

**Rectangle View**:
1. **Dynamic Rectangle**:
   - Width = f(x)
   - Height = g(x)
   - Visualized as actual rectangle
2. **x Slider**: Change input value
3. **Function Selectors**: Choose f(x) and g(x) from presets
4. **Dimension Labels**: Show f(x) = [value], g(x) = [value]
5. **Area Display**: Show area = f(x) × g(x)

**Change Decomposition Animation**:
1. **Δx Control**: Small increment slider
2. **Animate Change Button**: Show rectangle growing
3. **Color-Coded Regions**:
   - Original area: base color
   - f · Δg region (horizontal strip): color A
   - g · Δf region (vertical strip): color B
   - Δf · Δg corner (tiny square): faded color
4. **Contribution Labels**: Show each term's contribution to total area change
5. **As Δx → 0**: Animate shrinking, corner term disappearing

**Formula Build-Up**:
1. **Step-by-Step Display**:
   - Total change ≈ f·Δg + g·Δf + Δf·Δg
   - Divide by Δx
   - As Δx→0: f·g' + g·f'
2. **Interactive Equation**: Terms highlight as regions highlight

**Function Graph View** (side panel):
1. **Plot f(x), g(x), h(x) = f(x)g(x)**: Three curves
2. **Tangent Lines**: Show derivatives visually
3. **Verify Formula**: Show h'(x) computed both ways

**Visual Design Requirements**:
- Rectangle clearly visible with gridlines
- Distinct colors for each contribution region
- Smooth animation of rectangle dimensions changing
- Labels directly on visualization
- Clear connection between area terms and formula terms

**Code Architecture Requirements**:
- Rectangle geometry with dynamic sizing
- Region highlighting system
- Animation sequence controller
- Formula rendering (possibly HTML overlay)

**Deliverables**:
Complete TypeScript implementation with interactive rectangle, animated decomposition, and formula display.
```
