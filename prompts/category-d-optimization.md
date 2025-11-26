# Category D: Optimisation Concepts — LLM Prompts

> **Target Audience**: Software developers with limited mathematics background  
> **Tech Stack**: Three.js, TypeScript  
> **Complexity**: Polished, production-quality code  
> **Purpose**: Educational portfolio demonstrating ML/AI concepts visually

---

## D1: Gradient Descent Variants

### D1 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Gradient Descent Optimizers — From Vanilla to Adam

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see vanilla gradient descent, momentum, RMSprop, and Adam compared on the same loss surface, watching momentum escape local minima.

**Prerequisites the learner should already understand**:
- Gradient descent basics (B3)
- Loss functions (C5)
- What learning rate means

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand vanilla gradient descent and its limitations
2. Know how momentum accumulates velocity
3. Understand RMSprop's adaptive learning rates
4. See Adam as combining momentum and RMSprop
5. Know when to use each optimizer

**Required Sections**:
1. **Vanilla Gradient Descent**:
   - Update rule: θ = θ - α∇L
   - Problems: slow in ravines, stuck in local minima, sensitive to learning rate
2. **Momentum**:
   - Intuition: ball rolling downhill gains speed
   - Update rule with velocity term
   - v = βv + ∇L; θ = θ - αv
   - Dampens oscillations, accelerates in consistent directions
   - Can escape shallow local minima
3. **RMSprop (Root Mean Square Propagation)**:
   - Problem: different parameters need different learning rates
   - Adapt learning rate per parameter
   - Track squared gradient moving average
   - Divide gradient by sqrt of this average
   - Works well for non-stationary problems
4. **Adam (Adaptive Moment Estimation)**:
   - Best of both: momentum + adaptive rates
   - First moment (mean of gradients) = momentum
   - Second moment (variance of gradients) = RMSprop
   - Bias correction for early steps
   - Default choice for most deep learning
5. **Comparison Table**: Memory, computation, hyperparameters, typical use
6. **Why This Matters for ML/AI**:
   - Optimizer choice significantly affects training
   - Adam usually "just works"
   - Understanding helps diagnose training problems

**Tone**: Focus on intuition and practical guidance. Formulas are secondary to understanding.

**Length**: Approximately 2000-2500 words with clear comparisons and use-case guidance.
```

### D1 — Three.js Visualization Prompt

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

---

## D2: Learning Rate Effects

### D2 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Learning Rate — The Most Important Hyperparameter

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will use an interactive slider to see: too small (slow), just right (convergent), too large (divergent) learning rates with real-time descent paths.

**Prerequisites the learner should already understand**:
- Gradient descent (B3, D1)
- What loss functions measure

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand learning rate as step size
2. See the symptoms of learning rate too small
3. See the symptoms of learning rate too large
4. Know strategies for finding good learning rates
5. Understand learning rate schedules

**Required Sections**:
1. **What is Learning Rate?** — Step size in parameter update
2. **Too Small**:
   - Symptoms: very slow convergence, gets stuck
   - Loss decreases but painfully slowly
   - Might not reach minimum in reasonable time
3. **Just Right**:
   - Steady, consistent descent
   - Loss decreases smoothly
   - Reaches good minimum efficiently
4. **Too Large**:
   - Symptoms: overshooting, oscillation, divergence
   - Loss increases or bounces around
   - May never converge
   - Can explode to infinity
5. **Finding Good Learning Rates**:
   - Learning rate finder (1cycle policy)
   - Start small, increase until loss explodes
   - Typical ranges for different optimizers
6. **Learning Rate Schedules**:
   - Step decay: reduce at fixed epochs
   - Exponential decay: continuous reduction
   - Cosine annealing: smooth decrease and increase
   - Warmup: start small, increase, then decay
7. **Why This Matters for ML/AI**:
   - Wrong learning rate = training failure
   - Often the first thing to tune
   - Adaptive optimizers help but don't solve everything

**Tone**: Practical and diagnostic. Help learners recognize symptoms in their own training.

**Length**: Approximately 1600-2000 words with clear visual descriptions of each scenario.
```

### D2 — Three.js Visualization Prompt

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

---

## D3: Batch vs Stochastic vs Mini-batch

### D3 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Batch, Stochastic, and Mini-batch Gradient Descent

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see how gradient estimate noise/accuracy differs between variants and how this affects the descent path.

**Prerequisites the learner should already understand**:
- Gradient descent basics (D1, D2)
- Loss as average over data points

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand batch GD uses all data per step
2. Understand stochastic GD uses one sample per step
3. Understand mini-batch GD as the practical middle ground
4. Know the trade-offs: accuracy vs speed vs noise
5. See how noise can help escape local minima

**Required Sections**:
1. **The Dataset Setting** — Loss is average over many data points
2. **Batch (Full) Gradient Descent**:
   - Compute gradient using ALL data
   - Accurate gradient estimate
   - Slow: must process entire dataset per step
   - Memory intensive
   - Smooth descent path
3. **Stochastic Gradient Descent (SGD)**:
   - Compute gradient using ONE sample
   - Noisy gradient estimate
   - Fast: one sample per step
   - Memory efficient
   - Zigzag descent path
   - Noise can escape local minima!
4. **Mini-batch Gradient Descent**:
   - Compute gradient using SUBSET of data (e.g., 32, 64, 128 samples)
   - Balanced noise vs accuracy
   - Efficient: vectorized operations on batch
   - The standard in practice
5. **Batch Size Effects**:
   - Larger batch = more accurate gradient, less noise
   - Smaller batch = more noise, faster updates
   - Very large batches can generalize poorly
6. **Why This Matters for ML/AI**:
   - Mini-batch is universal in deep learning
   - Batch size is a key hyperparameter
   - Some noise is actually beneficial

**Tone**: Clarify the confusing terminology (SGD often means mini-batch in practice). Practical focus.

**Length**: Approximately 1500-1800 words with clear comparisons.
```

### D3 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: D3
**Title**: Batch vs Stochastic vs Mini-batch
**Description**: Gradient estimate noise/accuracy differences affecting descent path.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands gradient descent

**Learning Objectives the visualization must support**:
1. See smooth path with batch GD
2. See noisy path with stochastic GD
3. See moderate noise with mini-batch
4. Understand trade-off between accuracy and speed

**Required Interactive Features**:

**Dataset View**:
1. **Data Points**: Scatter plot of synthetic data (e.g., 100-500 points)
2. **Model Line/Curve**: Current model prediction
3. **Individual Losses**: Option to show loss per data point

**Gradient Descent Comparison**:
1. **Three Simultaneous Runs**:
   - Batch (all data): smooth path
   - Stochastic (1 sample): noisy path
   - Mini-batch (configurable): moderate noise
2. **Color-Coded Paths**: Distinct colors for each variant
3. **Same Starting Point**: Fair comparison

**Loss Surface View**:
1. **2D Parameter Space**: Contour plot
2. **True Loss Surface**: Based on full dataset
3. **Estimated Gradient Arrows**: Show gradient estimate for each variant
4. **Gradient Noise Visualization**: Show how estimated gradients vary

**Batch Size Control**:
1. **Mini-batch Size Slider**: 1 (SGD) to full dataset (batch)
2. **Real-Time Path Update**: See path change with batch size
3. **Current Sample Highlight**: Show which samples are being used

**Speed vs Accuracy Panel**:
1. **Steps per Second**: Show update frequency
2. **Gradient Variance**: Show noise level
3. **Time to Convergence**: Estimated time comparison

**Noise Benefits Demo**:
1. **Local Minimum Surface**: Surface with trap
2. **Watch SGD Escape**: Noise helps jump out
3. **Batch Gets Stuck**: Smooth path goes into trap

**Animation Controls**:
1. **Play/Pause/Step**: Standard controls
2. **Speed Control**: Adjust animation speed
3. **Reset**: Return to start

**Visual Design Requirements**:
- Data points clearly visible
- Paths with different dash patterns or colors
- Gradient arrows showing direction and magnitude
- Noise level indicator (maybe oscillation amplitude)
- Clear legend

**Code Architecture Requirements**:
- Synthetic data generator
- Loss computation with sample subsets
- Gradient estimation with configurable batch size
- Path rendering with noise visualization
- Comparison metrics tracking

**Deliverables**:
Complete TypeScript implementation with data view, three-way comparison, batch size control, and noise benefit demonstration.
```

---

## D4: Regularisation Visualised

### D4 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Regularisation — L1 and L2 Penalties

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see L1 (diamond) vs L2 (circle) constraint regions and understand why L1 promotes sparsity.

**Prerequisites the learner should already understand**:
- Loss functions (C5)
- Gradient descent (D1)
- What overfitting means

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand regularisation as a constraint on weights
2. Know L2 regularisation (Ridge, weight decay)
3. Know L1 regularisation (Lasso)
4. Visualize constraint regions geometrically
5. Understand why L1 gives sparse solutions

**Required Sections**:
1. **The Overfitting Problem** — Model fits training data too well, fails on new data
2. **Regularisation Idea** — Penalize large weights to keep model simple
3. **L2 Regularisation (Ridge)**:
   - Add ||w||² to loss
   - Penalty grows quadratically with weight magnitude
   - Constraint region is a circle/sphere
   - Pushes weights toward zero but rarely exactly zero
   - Also called "weight decay"
4. **L1 Regularisation (Lasso)**:
   - Add ||w||₁ to loss
   - Penalty grows linearly with weight magnitude
   - Constraint region is a diamond
   - Pushes weights to EXACTLY zero (sparsity!)
   - Feature selection effect
5. **The Geometric Intuition**:
   - Loss contours want to expand
   - Constraint region limits expansion
   - Optimal point where contour touches constraint
   - Diamond corners touch first → sparse solution
6. **Combined (Elastic Net)** — Mix of L1 and L2
7. **Why This Matters for ML/AI**:
   - Regularisation prevents overfitting
   - L2 is default (weight decay in optimizers)
   - L1 for feature selection or when sparsity desired
   - Trade-off via regularisation strength (λ)

**Tone**: Focus heavily on the geometric intuition. The "why L1 = sparsity" insight is the key takeaway.

**Length**: Approximately 1600-2000 words with geometric explanations.
```

### D4 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: D4
**Title**: Regularisation Visualised
**Description**: L1 diamond vs L2 circle constraints. Why L1 promotes sparsity.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands loss functions and optimization

**Learning Objectives the visualization must support**:
1. See L2 constraint as circle, L1 as diamond
2. Watch loss contours expand to meet constraint
3. See L1 hitting corners (sparse solutions)
4. See L2 touching smooth boundary (dense solutions)
5. Understand regularisation strength effect

**Required Interactive Features**:

**2D Parameter Space**:
1. **Two Weights**: w₁ on x-axis, w₂ on y-axis
2. **Loss Contours**: Elliptical contours of unregularised loss
3. **Constraint Region**:
   - L2: Circle ||w||² ≤ c
   - L1: Diamond ||w||₁ ≤ c
   - Toggle between them
4. **Optimal Point**: Where contour meets constraint

**Constraint Visualization**:
1. **Regularisation Toggle**: L1 / L2 / Both
2. **Strength Slider (λ)**: Adjusts constraint size
3. **Animation**: Watch constraint shrink as λ increases
4. **Optimal Point Movement**: See solution move with λ

**Sparsity Demonstration**:
1. **L1 Focus**: Show corner-hitting behavior
2. **Rotate Loss Contours**: Different loss orientations
3. **Corner Preference**: Highlight how often L1 hits corners
4. **L2 Comparison**: Same loss orientation, different solution

**Side-by-Side View**:
1. **L1 Panel**: Diamond constraint with optimal point
2. **L2 Panel**: Circle constraint with optimal point
3. **Synchronized Contours**: Same loss in both
4. **Weight Value Display**: Show w₁, w₂ values for each

**Regularisation Path**:
1. **λ Sweep**: Animate λ from 0 to large
2. **Solution Path**: Trace how optimal point moves
3. **Sparsity Indicator**: Show when weights hit zero (L1)

**Interactive Loss**:
1. **Drag Loss Center**: Move optimal unregularised point
2. **Adjust Eccentricity**: Change loss contour shape
3. **See Effect**: Watch regularised solution change

**Visual Design Requirements**:
- Clear constraint boundaries (L1 diamond, L2 circle)
- Concentric loss contours with labels
- Highlighted optimal point with coordinate display
- Distinct colors for L1 vs L2 regions
- Animation showing constraint/contour interaction

**Code Architecture Requirements**:
- Loss contour computation
- Constraint boundary rendering
- Constrained optimization (find touching point)
- Animation for λ sweep
- Dual-view synchronization

**Deliverables**:
Complete TypeScript implementation with constraint visualization, sparsity demonstration, and regularisation path animation.
```

---

## Summary

| ID | Title | Education Prompt | Visualization Prompt |
|----|-------|------------------|---------------------|
| D1 | Gradient Descent Variants | ✅ | ✅ |
| D2 | Learning Rate Effects | ✅ | ✅ |
| D3 | Batch vs Stochastic vs Mini-batch | ✅ | ✅ |
| D4 | Regularisation Visualised | ✅ | ✅ |
