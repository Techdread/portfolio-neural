# Category F: Training Dynamics — LLM Prompts

> **Target Audience**: Software developers with limited mathematics background  
> **Tech Stack**: Three.js, TypeScript, TensorFlow.js (where applicable)  
> **Complexity**: Polished, production-quality code  
> **Purpose**: Educational portfolio demonstrating ML/AI concepts visually

---

## F1: Loss Landscape Terrain

### F1 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Loss Landscapes — Visualizing the Optimization Terrain

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see the loss surface as 3D terrain with gradient descent visualized as a ball rolling downhill.

**Prerequisites the learner should already understand**:
- Loss functions (C5)
- Gradient descent (D1)
- What parameters/weights are

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand loss landscape as terrain over parameter space
2. Visualize optimization as descending this terrain
3. Know about local minima, global minima, and saddle points
4. Understand why deep networks have complex landscapes
5. Connect landscape shape to optimization difficulty

**Required Sections**:
1. **Loss as Function of Parameters** — Every weight combination = one loss value
2. **The Terrain Metaphor**:
   - 2D parameter space = 3D surface (simple model)
   - Height = loss value
   - Lower = better
   - Goal: find the lowest point
3. **Types of Critical Points**:
   - Global minimum: absolute lowest (ideal)
   - Local minima: lowest nearby, but not overall
   - Saddle points: minimum in some directions, maximum in others
   - Plateaus: flat regions with near-zero gradient
4. **Why Landscapes Are Complex**:
   - High-dimensional (millions of weights)
   - Non-convex (many bumps and valleys)
   - Surprisingly, many local minima are "good enough"
5. **Gradient Descent as Ball Rolling**:
   - Gradient = slope = direction ball would roll
   - Step size = learning rate
   - Momentum = ball's velocity carrying it further
6. **Landscape Challenges**:
   - Getting stuck in local minima
   - Slow progress on plateaus
   - Saddle points (common in high dimensions)
   - Sharp vs flat minima (generalization)
7. **Why This Matters for ML/AI**:
   - Understanding landscape helps diagnose training problems
   - Flat minima may generalize better
   - Modern networks are easier to optimize than expected

**Tone**: Make it visual and physical. The terrain metaphor should be central.

**Length**: Approximately 1600-2000 words with vivid landscape descriptions.
```

### F1 — Three.js Visualization Prompt

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

---

## F2: Backprop Gradient Flow

### F2 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Gradient Flow in Backpropagation — Vanishing and Exploding Gradients

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see gradients flowing backwards through a network, color-coded by magnitude, revealing vanishing and exploding gradient problems.

**Prerequisites the learner should already understand**:
- Backpropagation basics (C2)
- Chain rule (B4)
- Activation functions (C4)

**Learning Objectives** — After reading this explanation, the learner should:
1. Visualize gradients flowing through layers
2. Understand gradient magnitude changes layer by layer
3. Know what vanishing gradients look like
4. Know what exploding gradients look like
5. Understand solutions (ReLU, residual connections, normalization)

**Required Sections**:
1. **Gradient Flow Recap** — Gradients multiply through layers (chain rule)
2. **Layer-by-Layer Multiplication**:
   - Each layer contributes a factor
   - Final gradient = product of all factors
3. **Vanishing Gradients**:
   - When factors < 1 repeatedly
   - Gradient shrinks exponentially
   - Early layers get near-zero gradients
   - Weights stop learning
   - Common with sigmoid/tanh
4. **Exploding Gradients**:
   - When factors > 1 repeatedly
   - Gradient grows exponentially
   - Weights update too much
   - Training becomes unstable (NaN)
   - Common in RNNs
5. **Diagnosing the Problem**:
   - Gradient histograms
   - Loss curves (stuck or exploding)
   - Weight update magnitudes
6. **Solutions**:
   - ReLU activation (gradient is 0 or 1)
   - Proper initialization (Xavier, He)
   - Batch normalization
   - Residual connections (skip connections)
   - Gradient clipping (for exploding)
7. **Why This Matters for ML/AI**:
   - Vanishing gradients = can't train deep networks
   - Solutions enabled modern deep learning
   - Understanding helps debug training issues

**Tone**: Focus on the visual intuition of gradients "dying" or "exploding" through layers.

**Length**: Approximately 1800-2200 words with clear problem-solution structure.
```

### F2 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: F2
**Title**: Backprop Gradient Flow
**Description**: Gradients flowing backwards, color-coded by magnitude. Show vanishing/exploding.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands backpropagation basics

**Learning Objectives the visualization must support**:
1. See gradients flow backward layer by layer
2. Watch gradient magnitude change through network
3. Observe vanishing gradient (fading)
4. Observe exploding gradient (brightening)

**Required Interactive Features**:

**Network Display**:
1. **Deep Network Architecture**: 5-10 layers configurable
2. **Layer Blocks**: Visual representation of each layer
3. **Connection Lines**: Between layers
4. **Neuron Representation**: Simplified or detailed view

**Gradient Flow Animation**:
1. **Backward Flow**: Gradient pulses traveling from output to input
2. **Color Coding**: 
   - Bright = large gradient
   - Dim = small gradient
   - Red alert = exploding (too large)
3. **Magnitude Labels**: Numeric values at each layer
4. **Flow Speed**: Adjustable animation speed

**Configuration Panel**:
1. **Activation Selector**: Sigmoid, Tanh, ReLU, Leaky ReLU
2. **Layer Count**: Adjust depth (2 to 15 layers)
3. **Weight Initialization**: Random, Xavier, He
4. **Initial Gradient**: Set starting gradient magnitude

**Vanishing Demo**:
1. **Preset: Sigmoid Deep Network**: 10+ layers with sigmoid
2. **Watch Gradient Fade**: Color dims toward early layers
3. **Gradient Chart**: Bar chart of gradient magnitude per layer

**Exploding Demo**:
1. **Preset: Bad Initialization**: Large weights, deep network
2. **Watch Gradient Grow**: Color intensifies backward
3. **NaN Warning**: Alert when gradient explodes

**Solution Comparisons**:
1. **Toggle ReLU**: Switch activation, see improved flow
2. **Add Skip Connection**: Show residual path with preserved gradient
3. **Add Batch Norm**: Show normalized gradient flow
4. **Gradient Clipping**: Cap exploding gradients

**Histogram View**:
1. **Gradient Distribution**: Histogram of gradient values
2. **Per-Layer Histograms**: Side-by-side comparison
3. **Healthy vs Unhealthy**: Reference for good distribution

**Visual Design Requirements**:
- Gradient magnitude as color intensity + glow
- Clear layer separation
- Animated flow from right to left
- Warning indicators for problematic gradients
- Clean chart displays

**Code Architecture Requirements**:
- Network simulation with forward/backward pass
- Gradient computation per layer
- Animation sequencing
- Multiple preset configurations
- Real-time magnitude tracking

**Deliverables**:
Complete TypeScript implementation with gradient flow visualization, problem demos, and solution comparisons.
```

---

## F3: Weight Initialisation Comparison

### F3 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Weight Initialization — Starting Training Right

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will compare Xavier, He, and random initialization, seeing how activation distributions evolve through layers over epochs.

**Prerequisites the learner should already understand**:
- Neural network basics (C1)
- Activation functions (C4)
- Gradient flow (F2)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand why initialization matters
2. Know the problem with naive random initialization
3. Understand Xavier initialization and when to use it
4. Understand He initialization and when to use it
5. See how initialization affects activation distributions

**Required Sections**:
1. **Why Initialization Matters**:
   - Too small weights: signals vanish through layers
   - Too large weights: signals explode or saturate
   - Gradient flow depends on activation magnitudes
2. **Naive Random Initialization**:
   - Just random numbers
   - Usually causes problems
   - Activations shrink or explode layer by layer
3. **The Variance Problem**:
   - Output variance depends on input variance × weight variance × fan_in
   - Want output variance ≈ input variance (stable)
4. **Xavier/Glorot Initialization**:
   - Scale weights by 1/√(fan_in + fan_out)
   - Keeps variance stable for linear/tanh/sigmoid
   - Default for most activations
5. **He/Kaiming Initialization**:
   - Scale weights by √(2/fan_in)
   - Designed for ReLU (which zeros half the values)
   - Use with ReLU and variants
6. **Practical Guidelines**:
   - Use He for ReLU/Leaky ReLU
   - Use Xavier for tanh/sigmoid
   - Modern frameworks handle this automatically
7. **Why This Matters for ML/AI**:
   - Bad initialization = training failure or slow convergence
   - Good initialization = faster, more stable training
   - One of the key breakthroughs for deep learning

**Tone**: Practical focus. Show the problem, then the solution. Don't dwell on derivations.

**Length**: Approximately 1500-1800 words with clear recommendations.
```

### F3 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: F3
**Title**: Weight Initialisation Comparison
**Description**: Xavier, He, random — activation distributions through layers over epochs.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands activations and gradient flow

**Learning Objectives the visualization must support**:
1. See how different initializations affect activations
2. Watch activation distributions evolve during training
3. Compare stable vs unstable distributions
4. Understand Xavier vs He vs random

**Required Interactive Features**:

**Network View**:
1. **Multi-Layer Network**: 5-8 layer visualization
2. **Layer Blocks**: Each layer represented
3. **Activation Histograms**: Distribution at each layer
4. **Connection Lines**: Showing data flow

**Initialization Selector**:
1. **Random (Naive)**: Uniform or normal without scaling
2. **Xavier/Glorot**: Properly scaled for tanh/sigmoid
3. **He/Kaiming**: Properly scaled for ReLU
4. **Custom**: Manual variance input
5. **Apply Button**: Reinitialize network

**Comparison Mode**:
1. **Side-by-Side**: Two networks with different initializations
2. **Same Input**: Feed identical data to both
3. **Synchronized Layers**: Aligned for comparison

**Activation Distribution Display**:
1. **Per-Layer Histograms**: Distribution of activations
2. **Animation Over Layers**: Watch distribution change as data passes through
3. **Variance Indicator**: Show variance shrinking or growing
4. **Saturation Warning**: Highlight when activations are all near 0 or 1

**Training Simulation**:
1. **Epoch Slider**: Jump to different training epochs
2. **Animate Training**: Watch distributions evolve over epochs
3. **Gradient Magnitudes**: Show gradient health alongside
4. **Loss Curve**: Track training progress

**Activation Function Integration**:
1. **Activation Selector**: ReLU, Sigmoid, Tanh
2. **Initialization Recommendation**: Highlight best init for chosen activation
3. **Show Mismatch**: Demo Xavier with ReLU (suboptimal)

**Statistics Panel**:
1. **Layer-by-Layer Variance**: Numeric values
2. **Dead Neuron Count**: For ReLU (neurons stuck at 0)
3. **Saturation Percentage**: For sigmoid/tanh

**Visual Design Requirements**:
- Clean histogram visualization
- Color gradient for healthy/unhealthy distributions
- Clear layer labels
- Smooth animation for training evolution
- Side-by-side comparison layout

**Code Architecture Requirements**:
- Initialization function implementations
- Forward pass simulation
- Histogram computation
- Training loop simulation
- Multi-network state management

**Deliverables**:
Complete TypeScript implementation with initialization options, distribution visualization, training simulation, and comparison mode.
```

---

## F4: Overfitting Visualised

### F4 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Overfitting — When Your Model Memorizes Instead of Learns

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see training vs validation loss diverging and watch decision boundaries become overly complex.

**Prerequisites the learner should already understand**:
- Training and loss concepts (C5)
- What a decision boundary is (hyperplane separating classes)
- Basic idea of generalization

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand overfitting as memorizing training data
2. Know the train/validation loss divergence signature
3. See overfitting as overly complex decision boundaries
4. Know strategies to prevent overfitting
5. Understand the bias-variance tradeoff conceptually

**Required Sections**:
1. **What is Overfitting?**:
   - Model performs great on training data
   - Model performs poorly on new data
   - Has memorized rather than generalized
2. **The Train/Validation Gap**:
   - Training loss keeps decreasing
   - Validation loss starts increasing
   - Gap = overfitting
3. **Visual Signs**:
   - Decision boundary hugs every training point
   - Wiggly, complex boundaries
   - Fits noise, not signal
4. **Causes of Overfitting**:
   - Model too complex for data
   - Training too long
   - Too little training data
   - No regularization
5. **Prevention Strategies**:
   - Early stopping (stop before validation loss rises)
   - Regularization (L1, L2)
   - Dropout (randomly disable neurons)
   - Data augmentation (more training data)
   - Simpler model architecture
6. **Bias-Variance Tradeoff**:
   - Underfitting (high bias): too simple
   - Overfitting (high variance): too complex
   - Sweet spot: balanced
7. **Why This Matters for ML/AI**:
   - Overfitting is the central challenge
   - All practitioners must monitor and prevent it
   - Defines the whole field's approach to model evaluation

**Tone**: Use clear visual language. The "memorizing vs learning" metaphor is key.

**Length**: Approximately 1600-2000 words with practical prevention tips.
```

### F4 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: F4
**Title**: Overfitting Visualised
**Description**: Training vs validation loss diverging. Decision boundary becoming too complex.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable), TensorFlow.js (optional for real training)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands loss functions and training

**Learning Objectives the visualization must support**:
1. See training/validation loss curves diverge
2. Watch decision boundary evolve from simple to overfit
3. Identify the optimal stopping point
4. Understand regularization effect

**Required Interactive Features**:

**Data Display**:
1. **2D Scatter Plot**: Training data points (two classes)
2. **Validation Points**: Distinct markers for validation set
3. **Noise Level Slider**: Add noise to data
4. **Data Generation**: Create new random datasets

**Decision Boundary View**:
1. **Live Boundary**: Evolving as model trains
2. **Background Coloring**: Regions classified as each class
3. **Complexity Indicator**: Measure of boundary complexity
4. **Optimal vs Overfit Comparison**: Side-by-side

**Loss Curves**:
1. **Dual Lines**: Training loss and validation loss
2. **Real-Time Update**: Curves grow as training progresses
3. **Divergence Point Marker**: Highlight where gap opens
4. **Optimal Stop Point**: Mark best validation loss

**Training Controls**:
1. **Train Button**: Start/pause training
2. **Epoch Slider**: Jump to specific epoch
3. **Training Speed**: Fast/slow animation
4. **Reset**: Start over

**Model Complexity Control**:
1. **Hidden Layers Slider**: 1 to 5 layers
2. **Neurons per Layer**: Adjust model capacity
3. **See Effect**: Watch boundary complexity change

**Regularization Demos**:
1. **No Regularization**: Baseline overfit
2. **L2 Regularization Slider**: Add weight decay
3. **Dropout Slider**: Add dropout rate
4. **Early Stopping**: Auto-stop at best validation
5. **Compare Mode**: With vs without regularization

**Metrics Panel**:
1. **Train Accuracy**: Current training accuracy
2. **Validation Accuracy**: Current validation accuracy
3. **Gap Indicator**: Train - Validation difference
4. **Overfitting Alert**: Warning when gap is large

**Visual Design Requirements**:
- Clear scatter plot with class colors
- Smooth decision boundary rendering
- Loss curves with clear legend
- Highlighted divergence region
- Responsive layout for plots

**Code Architecture Requirements**:
- Simple neural network training loop
- Decision boundary computation
- Loss tracking and plotting
- Regularization implementations
- Dataset generation and splitting

**Deliverables**:
Complete TypeScript implementation with data visualization, training simulation, loss curves, and regularization comparison.
```

---

## Summary

| ID | Title | Education Prompt | Visualization Prompt |
|----|-------|------------------|---------------------|
| F1 | Loss Landscape Terrain | ✅ | ✅ |
| F2 | Backprop Gradient Flow | ✅ | ✅ |
| F3 | Weight Initialisation Comparison | ✅ | ✅ |
| F4 | Overfitting Visualised | ✅ | ✅ |
