# B4: Chain Rule Visualiser — Three.js Visualization Prompt

## Visualization ID
B4

## Title
Chain Rule Visualiser

## Description
Nested functions as pipeline. Animate derivatives multiplying through — the heart of backprop.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: B4
**Title**: Chain Rule Visualiser
**Description**: Nested functions as pipeline. Animate derivatives multiplying through — the heart of backprop.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic derivatives (B1)

**Learning Objectives the visualization must support**:
1. See function composition as a data pipeline
2. Watch forward pass flow through pipeline
3. See derivatives multiply backward through the chain
4. Understand the connection to neural network backpropagation

**Required Interactive Features**:

**Pipeline View**:
1. **Function Blocks**: Visual boxes representing functions in a chain
   - Default: 3 stages (input → g(x) → f(u) → output)
   - Expandable to more stages
2. **Block Labels**: Show function name and formula
3. **Connecting Arrows**: Data flow between blocks
4. **Add/Remove Blocks**: Button to extend or shorten the chain

**Forward Pass Animation**:
1. **Input Value Slider**: Set x value
2. **Play Forward Button**: Animate value flowing through pipeline
3. **Intermediate Values**: Show computed value at each stage
4. **Value Boxes**: Numeric display at each connection

**Backward Pass Animation**:
1. **Play Backward Button**: Animate derivatives flowing back
2. **Derivative Labels**: Show f'(...) at each stage
3. **Multiplication Visualization**:
   - Derivatives appear at each stage
   - Animate them multiplying together
   - Running product shown as it accumulates
4. **Final Derivative Display**: Show d(output)/dx = product of all derivatives

**Function Customization**:
1. **Preset Chains**:
   - Simple: (x+1)² — two functions
   - Medium: sin(x²+1) — three functions
   - Complex: exp(sin(x²)) — four functions
2. **Individual Function Selector**: Change each block's function
3. **Custom Input**: Type a composite function, auto-decompose into blocks

**Neural Network Mode** (bonus):
1. **Layer Representation**: Show chain as neural network layers
2. **Weight Labels**: Include weights in each "layer function"
3. **Gradient w.r.t. Weight**: Show how chain rule gives weight gradients

**Visual Design Requirements**:
- Horizontal pipeline layout (left to right for forward)
- Function blocks as rounded rectangles with distinct colors
- Animated "packet" traveling through pipeline
- Gradient flow shown as backward-moving highlights
- Clear numeric displays at each stage

**Code Architecture Requirements**:
- Function composition engine
- Symbolic or numeric differentiation
- Animation timeline with forward/backward modes
- Modular block components
- State management for current animation step

**Deliverables**:
Complete TypeScript implementation with pipeline visualization, forward/backward animations, and clear derivative multiplication display.
```
