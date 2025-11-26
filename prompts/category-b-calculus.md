# Category B: Calculus Essentials — LLM Prompts

> **Target Audience**: Software developers with limited mathematics background  
> **Tech Stack**: Three.js, TypeScript  
> **Complexity**: Polished, production-quality code  
> **Purpose**: Educational portfolio demonstrating ML/AI concepts visually

---

## B1: Derivative as Slope

### B1 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Derivative as Slope — Understanding Rate of Change

**Context**: This is part of an interactive Three.js visualization portfolio teaching neural network mathematics. The learner will see an interactive function with a draggable point showing the tangent line.

**Prerequisites the learner should already understand**:
- Basic coordinate systems (x-y graphs)
- What a function is (input → output)
- Slope of a straight line (rise/run)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the derivative as "instantaneous rate of change"
2. Visualize the derivative as the slope of the tangent line
3. Understand the limit definition intuitively (secant → tangent)
4. Read derivative notation (f'(x), df/dx, dy/dx)
5. Know basic derivative rules (power rule, constant rule)
6. Connect derivatives to gradient descent optimization

**Required Sections**:
1. **Slope Recap** — Rise over run for straight lines
2. **The Problem with Curves** — Slope changes at every point
3. **The Secant Line Approach** — Average rate of change between two points
4. **The Key Insight** — Move the points closer together, secant → tangent
5. **The Limit Definition** — f'(x) = lim(h→0) [f(x+h) - f(x)] / h
   - Explain without heavy formalism
   - "What slope do we approach as the gap shrinks to zero?"
6. **Tangent Line** — The line that just "touches" the curve at one point
7. **Derivative Notation**:
   - f'(x): "f prime of x"
   - df/dx: "derivative of f with respect to x"
   - dy/dx: Leibniz notation
8. **Basic Rules** (intuitive, not proof-heavy):
   - Constant: derivative is 0 (flat line)
   - Power rule: x^n → nx^(n-1)
   - Sum rule: derivative of sum = sum of derivatives
9. **Why This Matters for ML/AI**:
   - Loss functions are curves we want to minimize
   - Derivative tells us which direction is "downhill"
   - Gradient descent: step in direction opposite to derivative
   - Every neural network weight is adjusted based on derivatives

**Tone**: Build intuition progressively. Use animations described in words. Make the limit definition feel natural, not scary.

**Length**: Approximately 1800-2200 words with clear progression from slope to derivative.
```

### B1 — Three.js Visualization Prompt

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

---

## B2: Partial Derivatives

### B2 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Partial Derivatives — Derivatives of Multivariable Functions

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see a 3D surface with slices showing change along each axis independently.

**Prerequisites the learner should already understand**:
- Derivatives of single-variable functions (B1)
- 3D coordinate systems (x, y, z)
- Functions with multiple inputs

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand functions of multiple variables as surfaces
2. Know that partial derivatives measure change in one direction only
3. Visualize partial derivatives as slopes of slice curves
4. Read partial derivative notation (∂f/∂x)
5. Connect partial derivatives to how neural network weights are updated individually

**Required Sections**:
1. **From One Variable to Many** — f(x) → f(x, y) → f(x, y, z, ...)
2. **Visualizing f(x, y)** — Height above the xy-plane as a surface
3. **The Problem** — A surface has infinitely many directions to go
4. **The Solution: One Direction at a Time** — Hold all other variables constant
5. **Partial Derivative Definition**:
   - ∂f/∂x: "How does f change as x changes (y held fixed)?"
   - ∂f/∂y: "How does f change as y changes (x held fixed)?"
6. **The Slice Interpretation**:
   - Fix y = c, get a curve in the xz-plane
   - ∂f/∂x is the slope of that curve
7. **Notation**:
   - ∂ (curly d) vs d (straight d)
   - Subscript notation: fₓ, f_y
8. **Computing Partial Derivatives** — Same rules as regular derivatives, treat other variables as constants
9. **Why This Matters for ML/AI**:
   - Neural networks have millions of parameters
   - We need to know how loss changes with respect to EACH weight
   - Partial derivatives tell us: "If I tweak this one weight, how does loss change?"
   - Backpropagation computes ALL partial derivatives efficiently
10. **The Gradient Preview** — Collecting all partials into a vector (leads to B3)

**Tone**: Emphasize the "one direction at a time" intuition. Use the slice visualization heavily.

**Length**: Approximately 1600-2000 words with clear examples and connection to ML.
```

### B2 — Three.js Visualization Prompt

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

---

## B3: The Gradient Vector

### B3 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Gradient Vector — The Direction of Steepest Ascent

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see a 2D surface in 3D with an arrow pointing "uphill" and understand why the negative gradient is the direction of steepest descent.

**Prerequisites the learner should already understand**:
- Partial derivatives (B2)
- Vectors as arrows with direction and magnitude (A1)
- 3D surfaces from f(x, y)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the gradient as a vector of all partial derivatives
2. Know that the gradient points in the direction of steepest increase
3. Understand why negative gradient = steepest decrease
4. Know the gradient magnitude indicates steepness
5. Connect directly to gradient descent optimization

**Required Sections**:
1. **From Individual Partials to a Vector** — Collecting ∂f/∂x, ∂f/∂y into ∇f
2. **Gradient Notation**: ∇f = (∂f/∂x, ∂f/∂y) or grad(f)
3. **The Key Property** — Gradient points in direction of steepest increase
   - Intuitive explanation: gradient combines "uphill" information from all directions
4. **Gradient Magnitude** — How steep is the steepest direction?
   - Flat areas have small gradient
   - Steep areas have large gradient
5. **Negative Gradient** — Flip the arrow to go downhill
6. **Gradient in the xy-Plane** — The gradient is a 2D vector lying in the input space, not pointing up the surface
7. **Why This Matters for ML/AI**:
   - Loss function is a surface over weight space
   - We want to go downhill (minimize loss)
   - Gradient tells us the direction of steepest descent
   - Gradient descent: weights = weights - learning_rate × gradient
8. **Gradient for N Variables** — Extends to millions of weights
9. **Computing Gradients** — Backpropagation is just efficient gradient computation

**Tone**: Make the "direction of steepest ascent" intuition crystal clear. Use the hiking/terrain analogy.

**Length**: Approximately 1600-2000 words, with strong emphasis on the ML connection.
```

### B3 — Three.js Visualization Prompt

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

---

## B4: Chain Rule Visualiser

### B4 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Chain Rule — Derivatives of Composed Functions

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see nested functions as a pipeline with derivatives multiplying through — the heart of backpropagation.

**Prerequisites the learner should already understand**:
- Derivatives of basic functions (B1)
- Function composition: f(g(x))
- What multiplication represents

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand function composition as a pipeline/chain
2. Know the chain rule: d/dx[f(g(x))] = f'(g(x)) · g'(x)
3. Visualize derivatives "multiplying through" the chain
4. Understand why chain rule is THE foundation of backpropagation
5. Apply chain rule to multi-step computations

**Required Sections**:
1. **Function Composition Recap** — f(g(x)): "g processes x, then f processes the result"
2. **The Pipeline Metaphor** — Input flows through stages, each transforming it
3. **The Problem** — How does changing x affect the final output?
4. **Intuitive Chain Rule**:
   - If g doubles its input, and f triples its input...
   - Overall effect: 2 × 3 = 6× (derivatives multiply!)
5. **The Chain Rule Formula**:
   - d/dx[f(g(x))] = f'(g(x)) · g'(x)
   - "Derivative of outer times derivative of inner"
6. **Step-by-Step Example**:
   - h(x) = (3x + 1)²
   - Outer: f(u) = u², Inner: g(x) = 3x + 1
   - Work through completely
7. **Multiple Links in the Chain**:
   - f(g(h(x))): just keep multiplying
   - Each derivative evaluated at its input value
8. **Why This Matters for ML/AI**:
   - Neural network = composition of many functions
   - Forward pass: apply functions in sequence
   - Backward pass: multiply derivatives in reverse (backprop!)
   - Loss depends on weights through many layers
   - Chain rule connects loss to each weight
9. **The Computational Graph View** — Nodes are operations, edges are data flow

**Tone**: Make the "multiply through" intuition extremely clear. The pipeline metaphor is key.

**Length**: Approximately 2000-2400 words — this is critical for understanding backprop.
```

### B4 — Three.js Visualization Prompt

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

---

## B5: Product Rule

### B5 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Product Rule — Derivative of Multiplied Functions

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see the area of a rectangle analogy: d(uv) = u·dv + v·du with both terms animated.

**Prerequisites the learner should already understand**:
- Derivatives of single functions (B1)
- What multiplication of functions means: h(x) = f(x) × g(x)

**Learning Objectives** — After reading this explanation, the learner should:
1. Know the product rule formula: (fg)' = f'g + fg'
2. Understand the geometric interpretation (rectangle area)
3. Apply the product rule to compute derivatives
4. Know when and why the product rule is needed

**Required Sections**:
1. **The Setup** — Two functions multiplied: h(x) = f(x) · g(x)
2. **Why Not Just Multiply Derivatives?** — Show counterexample: (f·g)' ≠ f'·g'
3. **The Rectangle Analogy**:
   - Rectangle with width f(x) and height g(x)
   - Area = f(x) · g(x)
   - When x changes, both dimensions change!
   - Change in area = f·Δg + g·Δf + Δf·Δg (third term vanishes)
4. **The Product Rule Formula**:
   - (fg)' = f'g + fg' (Leibniz: d(uv) = u·dv + v·du)
   - "First times derivative of second, plus second times derivative of first"
5. **Worked Examples**:
   - h(x) = x² · sin(x)
   - h(x) = e^x · x
6. **Common Mistakes** — Don't just multiply the derivatives
7. **Why This Matters for ML/AI**:
   - Gating mechanisms: sigmoid · hidden state (LSTMs)
   - Attention: softmax weights × values
   - Loss functions with regularization terms
   - When backprop encounters multiplications

**Tone**: Focus on the rectangle intuition. Make the formula memorable with mnemonics.

**Length**: Approximately 1200-1500 words. Concise but thorough.
```

### B5 — Three.js Visualization Prompt

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

---

## B6: Sum Rule & Linearity

### B6 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Sum Rule and Linearity of Differentiation

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see derivatives distributing over addition — a simple but foundational concept.

**Prerequisites the learner should already understand**:
- Derivatives of single functions (B1)
- What adding functions means: h(x) = f(x) + g(x)

**Learning Objectives** — After reading this explanation, the learner should:
1. Know the sum rule: (f + g)' = f' + g'
2. Know the constant multiple rule: (cf)' = c · f'
3. Understand linearity: derivative of linear combination = linear combination of derivatives
4. See why this makes differentiation "nice"

**Required Sections**:
1. **Adding Functions** — h(x) = f(x) + g(x) means adding heights at each x
2. **The Sum Rule** — (f + g)' = f' + g'
   - Intuition: slopes add up
   - If f is increasing by 2 and g is increasing by 3, total is increasing by 5
3. **The Constant Multiple Rule** — (cf)' = c · f'
   - Scaling a function scales its derivative
   - Twice as steep everywhere
4. **Difference Rule** — (f - g)' = f' - g' (just sum rule with negative)
5. **Linearity Property**:
   - Derivative is a "linear operator"
   - d/dx[af(x) + bg(x)] = a·f'(x) + b·g'(x)
6. **Why This is Wonderful**:
   - Break complex functions into simpler pieces
   - Differentiate pieces separately
   - Combine the results
7. **Why This Matters for ML/AI**:
   - Neural network outputs are sums of weighted inputs
   - Gradients distribute over additions
   - Makes backprop through sum nodes trivial
   - Residual connections: gradient flows through addition unchanged

**Tone**: Keep it simple. This is foundational scaffolding for harder rules.

**Length**: Approximately 1000-1300 words. Brief and clear.
```

### B6 — Three.js Visualization Prompt

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

---

## Summary

| ID | Title | Education Prompt | Visualization Prompt |
|----|-------|------------------|---------------------|
| B1 | Derivative as Slope | ✅ | ✅ |
| B2 | Partial Derivatives | ✅ | ✅ |
| B3 | The Gradient Vector | ✅ | ✅ |
| B4 | Chain Rule Visualiser | ✅ | ✅ |
| B5 | Product Rule | ✅ | ✅ |
| B6 | Sum Rule & Linearity | ✅ | ✅ |
