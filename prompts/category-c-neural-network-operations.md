# Category C: Neural Network Operations — LLM Prompts

> **Target Audience**: Software developers with limited mathematics background  
> **Tech Stack**: Three.js, TypeScript, TensorFlow.js (where applicable)  
> **Complexity**: Polished, production-quality code  
> **Purpose**: Educational portfolio demonstrating ML/AI concepts visually

---

## C1: Forward Pass Step-by-Step

### C1 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Neural Network Forward Pass — Step by Step

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see data flowing through layers: input → weighted sum → activation → output, with actual numbers displayed.

**Prerequisites the learner should already understand**:
- Vectors and dot products (A1)
- Matrix multiplication (A2)
- What a function does (maps input to output)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand a neural network as layers of computations
2. Know what happens at each neuron: weighted sum + bias + activation
3. Trace exact numbers through a simple network
4. Understand why matrix multiplication handles all neurons in a layer at once
5. Know the difference between weights, biases, and activations

**Required Sections**:
1. **What is a Forward Pass?** — Data entering, flowing through, result coming out
2. **The Single Neuron**:
   - Receives multiple inputs
   - Each input multiplied by a weight
   - Sum all weighted inputs
   - Add a bias
   - Apply activation function
   - Formula: output = activation(w₁x₁ + w₂x₂ + ... + wₙxₙ + b)
3. **Why Weights and Biases?**:
   - Weights: importance of each input
   - Bias: shift the decision threshold
4. **Activation Functions** — Non-linearity introduction (brief, detailed in C4)
5. **From Neuron to Layer**:
   - A layer = many neurons receiving same inputs
   - Matrix multiplication does all neurons at once
   - output = activation(W · input + b)
6. **Multiple Layers**:
   - Output of layer 1 becomes input to layer 2
   - Stacking layers = composing functions
7. **Worked Example with Numbers**:
   - 2 inputs, 2 hidden neurons, 1 output
   - Show EVERY number at EVERY step
8. **Why This Matters for ML/AI**:
   - Prediction = one forward pass
   - Inference time = sum of layer computations
   - Understanding forward pass is prerequisite for backprop

**Tone**: Very concrete. Use actual numbers everywhere. Make the math tangible.

**Length**: Approximately 2000-2500 words with detailed worked example.
```

### C1 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C1
**Title**: Forward Pass Step-by-Step
**Description**: Data flowing through layers: input → weighted sum → activation → output. Show actual numbers.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands vectors, dot products, matrices

**Learning Objectives the visualization must support**:
1. See neurons as processing units receiving and sending values
2. Watch data flow step-by-step through the network
3. See exact numbers at every stage
4. Understand the sequence: input → weighted sum → bias → activation → output

**Required Interactive Features**:

**Network Structure**:
1. **Configurable Architecture**:
   - Default: 2 inputs → 3 hidden → 2 outputs
   - Adjustable layer count (1-4 layers)
   - Adjustable neurons per layer
2. **Neuron Display**: Circles/nodes representing neurons
3. **Connection Lines**: Lines between neurons showing weights
4. **Weight Labels**: Show weight value on each connection

**Input Controls**:
1. **Input Sliders**: Set each input value (-1 to 1)
2. **Preset Inputs**: Quick buttons for common test values
3. **Random Inputs**: Generate random input values

**Weight/Bias Controls**:
1. **Editable Weights**: Click to modify any weight
2. **Random Weights**: Initialize randomly
3. **Preset Networks**: Load pre-configured networks that demonstrate specific behaviors

**Step-by-Step Animation**:
1. **Full Auto Play**: Run entire forward pass with animation
2. **Step Forward Button**: Advance one computation at a time
3. **Step Back Button**: Go back to see previous state
4. **Speed Control**: Slow/medium/fast animation
5. **Current Step Indicator**: "Computing weighted sum for hidden neuron 2"

**Value Displays**:
1. **Neuron Values**: Show current value inside or beside each neuron
2. **Weighted Sum Breakdown**: On hover, show w₁x₁ + w₂x₂ + ... + b = sum
3. **Pre-Activation vs Post-Activation**: Show value before and after activation
4. **Formula Panel**: Display the formula being computed at current step

**Activation Function**:
1. **Function Selector**: ReLU, Sigmoid, Tanh, Linear
2. **Mini Graph**: Small plot of activation function beside each layer

**Visual Design Requirements**:
- Layered left-to-right layout (input → hidden → output)
- Animated "pulse" traveling along connections
- Color intensity on neurons based on activation value
- Positive weights in one color, negative in another
- Clear layer separation with labels

**Code Architecture Requirements**:
- Network class with configurable architecture
- Forward pass function with step-by-step mode
- Animation timeline system
- State management for replay/rewind
- Modular neuron and layer components

**Deliverables**:
Complete TypeScript implementation with full animation system, editable parameters, and clear numeric displays at every step.
```

---

## C2: Backpropagation Walkthrough

### C2 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Backpropagation — Computing Gradients Layer by Layer

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see error gradients flowing backwards with the chain rule at each node, accumulating gradients.

**Prerequisites the learner should already understand**:
- Forward pass (C1)
- The chain rule (B4)
- Partial derivatives (B2)
- The gradient as direction of change (B3)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand backprop as "reverse mode differentiation"
2. Know why we compute gradients from output to input
3. Trace gradient computation through a simple network
4. Understand how gradients accumulate at each weight
5. Connect chain rule multiplication to layer-by-layer gradient flow

**Required Sections**:
1. **The Goal of Backprop** — Compute ∂Loss/∂w for every weight w
2. **Why Backwards?** — Efficiency: one backward pass gives ALL gradients
3. **The Chain Rule Connection**:
   - Loss depends on output
   - Output depends on hidden layer
   - Hidden layer depends on weights
   - Chain them together!
4. **Step-by-Step Backprop**:
   - Start with ∂Loss/∂output (how loss changes with output)
   - Compute ∂output/∂hidden (through activation derivative)
   - Multiply through to get ∂Loss/∂hidden
   - Continue backward to inputs and weights
5. **The Local Gradient** — Each node knows its own derivative
6. **Gradient Accumulation** — When one node feeds multiple paths
7. **Worked Example with Numbers**:
   - Same network as C1
   - Show EXACT gradient numbers at each step
   - Final result: gradient for each weight
8. **Why This Matters for ML/AI**:
   - Backprop enables training of deep networks
   - Without it, we couldn't compute gradients efficiently
   - Autodiff libraries (PyTorch, TensorFlow) do this automatically
9. **Common Confusions**:
   - Backprop ≠ gradient descent (backprop computes, GD uses)
   - Why multiply, not add (chain rule)

**Tone**: Match the step-by-step concreteness of C1. Numbers at every step.

**Length**: Approximately 2200-2800 words with detailed worked example matching C1's network.
```

### C2 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C2
**Title**: Backpropagation Walkthrough
**Description**: Error gradients flowing backwards. Chain rule at each node, accumulating gradients.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User has completed C1 (Forward Pass)
- User understands chain rule (B4)

**Learning Objectives the visualization must support**:
1. See gradients flowing backward through the network
2. Watch chain rule multiplication at each node
3. See gradients accumulate at weights
4. Understand the forward/backward pass relationship

**Required Interactive Features**:

**Network Display** (same as C1):
1. **Same Architecture Options**: Match C1 for continuity
2. **Forward Pass First**: Complete forward pass before backward
3. **Loss Computation**: Show loss value after forward pass

**Backward Pass Animation**:
1. **Step-by-Step Mode**: One gradient computation at a time
2. **Current Gradient Highlight**: Show which gradient is being computed
3. **Flow Animation**: Gradient "pulse" traveling backward on connections
4. **Multiplication Visualization**: Show chain rule multiplication at each node

**Gradient Displays**:
1. **Neuron Gradients**: ∂L/∂(neuron output) shown at each neuron
2. **Weight Gradients**: ∂L/∂w shown on each connection
3. **Local Derivative**: Show local derivative at each node (activation derivative, etc.)
4. **Multiplication Breakdown**: Show gradient_in × local_derivative = gradient_out

**Chain Rule Panel**:
1. **Current Computation**: Display the chain rule equation being computed
2. **Substituted Values**: Show numeric values plugged in
3. **Result**: Show computed gradient value

**Comparison View**:
1. **Side-by-Side**: Forward values on left, gradients on right
2. **Symmetry Highlighting**: Show correspondence between forward and backward paths
3. **Color Coding**: Gradient magnitude as color intensity

**Interactive Elements**:
1. **Target Value Input**: Set desired output (for loss computation)
2. **Loss Function Selector**: MSE, Cross-Entropy
3. **Gradient Check**: Numerical gradient approximation to verify

**Visual Design Requirements**:
- Reverse flow direction clearly indicated (arrows)
- Gradient values in different color than forward values
- Gradient magnitude as line thickness on connections
- Clear "backward pass" label/indicator
- Smooth animations with appropriate timing

**Code Architecture Requirements**:
- Backward pass function with step-by-step mode
- Gradient storage per weight and neuron
- Chain rule computation at each node
- Synchronization with forward pass state
- Clear data structures for gradient flow

**Deliverables**:
Complete TypeScript implementation that continues from C1's forward pass, with detailed backward pass animation and gradient display.
```

---

## C3: Computational Graph

### C3 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Computational Graphs — The Structure Behind Autodiff

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see expression trees for functions and watch autodiff traverse them forwards and backwards.

**Prerequisites the learner should already understand**:
- Basic operations (add, multiply, etc.)
- Forward and backward pass concepts (C1, C2)
- Chain rule (B4)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand expressions as tree/graph structures
2. Know how autodiff libraries represent computations
3. Trace forward evaluation through a computational graph
4. Trace backward differentiation through the same graph
5. Understand why graphs enable automatic gradient computation

**Required Sections**:
1. **Expressions as Trees** — f(x,y) = x² + xy as a tree of operations
2. **Nodes and Edges**:
   - Leaf nodes: inputs and constants
   - Internal nodes: operations (+, ×, sin, etc.)
   - Edges: data flow
3. **Forward Mode** — Evaluate from leaves to root
4. **The Gradient Problem** — How to get derivatives automatically?
5. **Backward Mode (Reverse Mode Autodiff)**:
   - Start at root with gradient = 1
   - Propagate gradients backward using local rules
   - Each node type has a backward rule
6. **Local Gradient Rules**:
   - Addition: passes gradient unchanged to both inputs
   - Multiplication: gradient × other input
   - Power: gradient × n × x^(n-1)
7. **Why Graphs Enable Autodiff**:
   - Every computation recorded
   - Backward pass follows recorded path
   - PyTorch/TensorFlow build these graphs automatically
8. **Dynamic vs Static Graphs** — PyTorch (dynamic) vs old TensorFlow (static)
9. **Why This Matters for ML/AI**:
   - Neural networks ARE computational graphs
   - Autodiff = automatic backprop
   - Understanding graphs helps debug gradient issues

**Tone**: Build from simple expressions to complex ones. Emphasize the "automatic" nature.

**Length**: Approximately 1800-2200 words with multiple graph examples.
```

### C3 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C3
**Title**: Computational Graph Visualizer
**Description**: Expression trees for functions. Autodiff traversing forwards and backwards.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands forward/backward passes
- User understands chain rule

**Learning Objectives the visualization must support**:
1. See expressions as visual graphs
2. Watch values flow forward through operations
3. Watch gradients flow backward through operations
4. Understand local gradient rules for each operation type

**Required Interactive Features**:

**Graph Construction**:
1. **Preset Expressions**:
   - Simple: x² + y
   - Medium: x×y + sin(x)
   - Complex: (x + y)² × z
2. **Custom Expression Input**: Text box to enter formula
3. **Visual Graph Building**: Drag-and-drop node creation (advanced)

**Graph Display**:
1. **Tree Layout**: Operations as nodes, data flow as edges
2. **Node Types** (distinct shapes/colors):
   - Input nodes (circles)
   - Operation nodes (rectangles with symbol: +, ×, ^, sin)
   - Output node (diamond)
3. **Edge Labels**: Show data flowing on edges
4. **Expandable Nodes**: Click to see operation details

**Forward Evaluation**:
1. **Input Value Sliders**: Set values for input variables
2. **Animate Forward Button**: Watch evaluation flow leaves → root
3. **Step-by-Step Mode**: One operation at a time
4. **Value Labels**: Show computed value at each node after evaluation

**Backward Differentiation**:
1. **Start Backward Button**: Begin gradient propagation
2. **Gradient Flow Animation**: Watch gradients flow root → leaves
3. **Local Rule Display**: Show the backward rule being applied at each node
4. **Gradient Values**: Show ∂output/∂node at each node
5. **Final Gradients**: Display ∂output/∂x, ∂output/∂y, etc.

**Rule Reference Panel**:
1. **Operation List**: Show backward rule for each operation type
2. **Current Operation**: Highlight rule being used

**Visual Design Requirements**:
- Clear hierarchical graph layout (root at top or left)
- Distinct visual treatment for forward vs backward mode
- Animated flow along edges
- Node highlighting during computation
- Clean, readable formulas/values

**Code Architecture Requirements**:
- Expression parser (text → graph)
- Graph node classes with forward() and backward() methods
- Graph traversal algorithms
- Layout algorithm for graph visualization
- Animation sequencing system

**Deliverables**:
Complete TypeScript implementation with expression parsing, graph visualization, and animated forward/backward traversal.
```

---

## C4: Activation Functions Gallery

### C4 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Activation Functions — The Non-Linear Heart of Neural Networks

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see sigmoid, tanh, ReLU, Leaky ReLU, and GELU side-by-side with both function and derivative plots.

**Prerequisites the learner should already understand**:
- What a function does
- Derivatives as slopes (B1)
- Forward pass (C1)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand why non-linearity is essential (linear networks collapse)
2. Know the major activation functions by shape and behavior
3. Understand the derivative of each activation (crucial for backprop)
4. Know which activations to use when and why
5. Understand vanishing gradient problem with certain activations

**Required Sections**:
1. **Why Non-Linearity?** — Without it, any deep network = one linear layer
2. **The Activation Zoo** — For each function:
   - **Sigmoid (σ)**: formula, shape, range (0,1), use cases, problems
   - **Tanh**: formula, shape, range (-1,1), centered, better than sigmoid
   - **ReLU**: formula, shape, range [0,∞), computational efficiency, dead neurons
   - **Leaky ReLU**: formula, addresses dead neuron problem, small negative slope
   - **GELU**: formula (approximate), smooth, used in transformers
3. **Derivatives Matter**:
   - Sigmoid derivative: σ(x)(1-σ(x)), max at 0.25!
   - Tanh derivative: 1-tanh²(x), max at 1
   - ReLU derivative: 0 or 1, no vanishing!
   - Why derivative matters: backprop multiplies through these
4. **The Vanishing Gradient Problem**:
   - Sigmoid/tanh squash gradients toward 0
   - Many layers = many small multiplications → gradient vanishes
   - ReLU family avoids this (gradient is 0 or 1)
5. **Choosing Activations**:
   - Hidden layers: ReLU, Leaky ReLU, GELU
   - Output layer: depends on task (sigmoid for binary, softmax for multi-class, linear for regression)
6. **Modern Trends** — GELU in transformers, Swish/SiLU gaining popularity

**Tone**: Practical focus on when to use what. Don't just list formulas—explain implications.

**Length**: Approximately 2000-2500 words covering all major activations thoroughly.
```

### C4 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C4
**Title**: Activation Functions Gallery
**Description**: Side-by-side comparison of sigmoid, tanh, ReLU, Leaky ReLU, GELU. Show function AND derivative.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands functions and derivatives

**Learning Objectives the visualization must support**:
1. Compare activation function shapes visually
2. See derivatives alongside the functions
3. Understand output ranges
4. Explore behavior at different input values
5. See the vanishing gradient problem visually

**Required Interactive Features**:

**Gallery View**:
1. **Grid Layout**: All activation functions in a grid (2-3 per row)
2. **Each Cell Contains**:
   - Function name and formula
   - Function plot
   - Derivative plot
   - Output range indicator
3. **Hover for Details**: Expanded info on hover

**Comparison Mode**:
1. **Overlay Plot**: Selected functions on same axes
2. **Function Toggle**: Checkboxes to show/hide each function
3. **Derivative Toggle**: Show derivatives instead of functions
4. **Normalized View**: Scale to compare shapes despite different ranges

**Interactive Point**:
1. **Draggable x-value**: Move along x-axis
2. **Value Display**: Show f(x) for each function at current x
3. **Derivative Display**: Show f'(x) for each function
4. **Comparison Table**: Numeric values in a table at current x

**Vanishing Gradient Demo**:
1. **Chain Multiplication**: Show what happens when gradient passes through many layers
2. **Layer Slider**: 1 to 50 layers
3. **Gradient Magnitude Plot**: Show gradient shrinking (sigmoid) vs stable (ReLU)
4. **Visual Alert**: Warning when gradient effectively vanishes

**Parameter Variants**:
1. **Leaky ReLU Slope**: Slider for negative slope (0.01 to 0.3)
2. **ELU Alpha**: Slider for alpha parameter
3. **Softplus Beta**: Temperature parameter

**Visual Design Requirements**:
- Consistent color per function across all views
- Clear axis labels and grid lines
- Function formula displayed in LaTeX-style rendering
- Smooth curves with many sample points
- Responsive grid layout

**Code Architecture Requirements**:
- Activation function classes with forward() and derivative() methods
- Configurable plot component
- Comparison overlay renderer
- Gradient chain computation
- Parameter binding for variants

**Deliverables**:
Complete TypeScript implementation with gallery view, comparison mode, interactive exploration, and vanishing gradient demonstration.
```

---

## C5: Loss Function Landscapes

### C5 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Loss Functions — Measuring How Wrong Your Model Is

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will compare MSE, cross-entropy, and hinge loss surfaces and observe how they affect optimization behavior.

**Prerequisites the learner should already understand**:
- What a function does
- Gradient descent concept (wanting to minimize something)
- Basic probability (for cross-entropy)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand loss functions as the "score" we want to minimize
2. Know MSE and when to use it (regression)
3. Know cross-entropy and when to use it (classification)
4. Understand hinge loss (SVMs)
5. See how loss shape affects optimization

**Required Sections**:
1. **What is Loss?** — Quantifying "wrongness" with a single number
2. **Mean Squared Error (MSE)**:
   - Formula: (1/n)Σ(y - ŷ)²
   - Squaring penalizes large errors more
   - Used for regression tasks
   - Smooth, differentiable everywhere
3. **Cross-Entropy Loss**:
   - Formula: -Σy·log(ŷ)
   - From information theory
   - Used for classification
   - Harsh penalty for confident wrong predictions
   - Relates to likelihood maximization
4. **Binary vs Multi-class Cross-Entropy**:
   - Binary: -[y·log(ŷ) + (1-y)·log(1-ŷ)]
   - Multi-class: requires softmax outputs
5. **Hinge Loss**:
   - Formula: max(0, 1 - y·ŷ)
   - Used in SVMs
   - Margin-based: only penalizes within margin
6. **Loss Landscapes**:
   - How loss varies across parameter space
   - Convex vs non-convex
   - Local minima, saddle points
7. **Optimization Behavior**:
   - MSE: smooth gradients, steady descent
   - Cross-entropy: strong gradients far from correct, weak when close
   - Hinge: zero gradient outside margin
8. **Why This Matters for ML/AI**:
   - Loss function choice affects learning dynamics
   - Wrong loss = model optimizes wrong thing
   - Cross-entropy standard for classification, MSE for regression

**Tone**: Practical guidance on choosing loss functions. Use concrete examples.

**Length**: Approximately 1800-2200 words with clear comparisons.
```

### C5 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C5
**Title**: Loss Function Landscapes
**Description**: Compare MSE, cross-entropy, hinge loss surfaces and optimization behavior.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands optimization basics

**Learning Objectives the visualization must support**:
1. See different loss function shapes
2. Compare how loss responds to predictions
3. Watch optimization behave differently on each
4. Understand gradient magnitude differences

**Required Interactive Features**:

**1D Loss View** (prediction vs loss):
1. **Single Prediction Slider**: Move predicted value
2. **True Value Marker**: Fixed target value
3. **Loss Curves**: Plot all loss functions vs prediction
4. **Current Loss Point**: Marker showing loss at current prediction
5. **Gradient Arrow**: Show direction and magnitude of gradient

**2D Loss Surface** (two parameters):
1. **Surface Selector**: Choose which loss to display as 3D surface
2. **Parameter Axes**: Two weights/parameters on x-y plane
3. **Loss Height**: Z-axis as loss value
4. **Gradient Descent Path**: Watch optimizer traverse surface
5. **Comparison Mode**: Side-by-side surfaces for different losses

**Classification Focus**:
1. **Binary Classification Setup**: True class (0 or 1), predicted probability
2. **Cross-Entropy Plot**: Asymmetric curve showing harsh penalty
3. **Confidence Slider**: See how confident wrong predictions are penalized
4. **Comparison to MSE**: Overlay showing different gradients

**Multi-Parameter Landscape**:
1. **Simple Network**: 2-weight network for visualization
2. **Data Points**: Small dataset determining the loss surface
3. **Animate Training**: Watch weights move on loss surface
4. **Switch Loss Function**: See path change with different losses

**Visual Design Requirements**:
- 3D surfaces with height-based coloring
- Gradient vectors as arrows
- Training path as connected line with markers
- Side-by-side comparison layout
- Clear loss value displays

**Code Architecture Requirements**:
- Loss function classes (forward and gradient methods)
- Surface mesh generation from loss function
- Optimizer simulation
- Multiple synchronized views
- Comparison rendering system

**Deliverables**:
Complete TypeScript implementation with loss curves, 3D surfaces, gradient visualization, and training simulation.
```

---

## C6: Softmax & Cross-Entropy

### C6 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Softmax and Cross-Entropy — From Scores to Probabilities to Loss

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see logits transformed to probabilities and then to loss, with emphasis on the harsh penalty for confident wrong predictions.

**Prerequisites the learner should already understand**:
- Basic probability (numbers 0-1 summing to 1)
- Exponential function (e^x)
- Logarithm basics
- Loss functions concept (C5)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand logits as raw, unnormalized scores
2. Know how softmax converts logits to probabilities
3. Understand cross-entropy loss for multi-class classification
4. See why confident wrong predictions are severely penalized
5. Understand numerical stability (log-sum-exp trick)

**Required Sections**:
1. **The Classification Pipeline**: logits → softmax → probabilities → cross-entropy → loss
2. **What are Logits?** — Raw output scores, can be any real number
3. **Softmax Function**:
   - Formula: softmax(zᵢ) = e^zᵢ / Σⱼe^zⱼ
   - Properties: outputs sum to 1, all positive
   - Intuition: exponential makes bigger scores much bigger
   - Temperature parameter (optional)
4. **Why Softmax?**:
   - Differentiable (unlike argmax)
   - Preserves relative ordering
   - Gives probability interpretation
5. **Cross-Entropy Loss for Multi-class**:
   - Formula: L = -Σᵢyᵢlog(pᵢ) = -log(p_correct)
   - Only the correct class matters (one-hot encoding)
   - Minimizing = maximizing probability of correct class
6. **The Harsh Penalty**:
   - If model is confident AND wrong: -log(small number) = huge loss
   - If model is confident AND right: -log(large number) = small loss
   - Numerical example with extreme cases
7. **Numerical Stability**:
   - e^big number = overflow
   - log(small number) = -infinity
   - The log-sum-exp trick
8. **Why This Matters for ML/AI**:
   - Classification networks end with softmax
   - Cross-entropy is the standard classification loss
   - Understanding prevents debugging nightmares

**Tone**: Walk through the pipeline step by step. Make the log penalties intuitive.

**Length**: Approximately 1800-2200 words with numerical examples throughout.
```

### C6 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C6
**Title**: Softmax & Cross-Entropy
**Description**: Logits → probabilities → loss. Show harsh penalty for confident wrong predictions.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands probability basics
- User understands loss concepts (C5)

**Learning Objectives the visualization must support**:
1. See logits transform to probabilities via softmax
2. Watch probabilities become loss via cross-entropy
3. Understand the harsh penalty for confident wrong predictions
4. Explore temperature effects on softmax

**Required Interactive Features**:

**Pipeline View**:
1. **Logits Input**: Sliders for 3-5 class logits
2. **Softmax Step**: Visual transformation to probabilities
3. **Probability Bars**: Bar chart of output probabilities
4. **True Class Selector**: Pick which class is correct
5. **Cross-Entropy Calculation**: Show -log(p_correct) computation
6. **Final Loss Display**: Large, prominent loss value

**Softmax Exploration**:
1. **Individual Logit Sliders**: Change each independently
2. **Probability Response**: Watch probabilities shift
3. **Dominant Class Highlight**: Show which class "wins"
4. **Relative Difference Demo**: Show that only relative differences matter (subtract constant)

**Cross-Entropy Deep Dive**:
1. **Probability vs Loss Curve**: Plot -log(p) for p from 0 to 1
2. **Current Point Marker**: Show where current prediction sits on curve
3. **Harsh Penalty Zone**: Highlight region where loss explodes (p near 0)
4. **Confidence Slider**: Drag prediction probability, watch loss change

**Confident & Wrong Demo**:
1. **Scenario Presets**:
   - Confident correct: high prob on true class
   - Uncertain: roughly equal probs
   - Confident wrong: high prob on wrong class
2. **Loss Comparison**: Show dramatic difference in loss values
3. **Gradient Display**: Show how gradients differ in each case

**Temperature Control**:
1. **Temperature Slider**: τ from 0.1 to 10
2. **Effect Visualization**: Watch probability distribution sharpen or flatten
3. **Extreme Cases**: Near 0 → one-hot, high → uniform

**Visual Design Requirements**:
- Pipeline flowing left to right
- Bar charts for probabilities
- Loss value prominently displayed with color coding (red = high)
- -log(p) curve clearly plotted
- Smooth animations when logits change

**Code Architecture Requirements**:
- Softmax function with temperature
- Cross-entropy calculation
- Gradient computation (for display)
- Responsive bar chart rendering
- Animation for transitions

**Deliverables**:
Complete TypeScript implementation with interactive pipeline, probability visualization, and cross-entropy exploration.
```

---

## Summary

| ID | Title | Education Prompt | Visualization Prompt |
|----|-------|------------------|---------------------|
| C1 | Forward Pass Step-by-Step | ✅ | ✅ |
| C2 | Backpropagation Walkthrough | ✅ | ✅ |
| C3 | Computational Graph | ✅ | ✅ |
| C4 | Activation Functions Gallery | ✅ | ✅ |
| C5 | Loss Function Landscapes | ✅ | ✅ |
| C6 | Softmax & Cross-Entropy | ✅ | ✅ |
