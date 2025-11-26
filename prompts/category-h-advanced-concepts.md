# Category H: Advanced Concepts — LLM Prompts

> **Target Audience**: Software developers with limited mathematics background  
> **Tech Stack**: Three.js, TypeScript, TensorFlow.js (where applicable)  
> **Complexity**: Polished, production-quality code  
> **Purpose**: Educational portfolio demonstrating ML/AI concepts visually

---

## H1: Neural Style Transfer Live

### H1 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Neural Style Transfer — Blending Content and Style

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will watch the optimization process as content and style blend in real-time to create artistic images.

**Prerequisites the learner should already understand**:
- CNNs and feature maps (E1)
- Loss functions and optimization (C5, D1)
- What "features" means in neural networks

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand style transfer as an optimization problem
2. Know what content loss and style loss measure
3. Understand Gram matrices as style representation
4. See how the optimization gradually blends content and style
5. Know the difference from feedforward style transfer models

**Required Sections**:
1. **The Creative Goal** — Take content from one image, style from another
2. **Style Transfer as Optimization**:
   - Start with noise (or content image)
   - Optimize the pixels themselves
   - Minimize combined content + style loss
3. **Content Representation**:
   - CNN layers capture content at different levels
   - Higher layers = semantic content (objects, shapes)
   - Content loss = difference from target content features
4. **Style Representation**:
   - Style = textures, patterns, brushstrokes
   - Gram matrix: correlations between feature maps
   - Captures "which features occur together"
   - Style loss = Gram matrix difference across layers
5. **The Optimization Loop**:
   - Compute content loss (from content image)
   - Compute style loss (from style image)
   - Combined loss = α × content + β × style
   - Gradient descent on the output image pixels
6. **Watching it Evolve**:
   - Start: random noise or content
   - Early: structure emerges
   - Middle: style patterns appear
   - End: harmonious blend
7. **Trade-offs**:
   - α/β ratio controls content vs style strength
   - Layer choice affects result
   - More iterations = more refined
8. **Why This Matters for ML/AI**:
   - Demonstrates optimization beyond weights
   - Shows CNN features capture meaningful information
   - Foundation for many creative AI applications

**Tone**: Focus on the creative, artistic angle. Make the optimization feel like watching art being created.

**Length**: Approximately 1700-2100 words with emphasis on the visual evolution process.
```

### H1 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: H1
**Title**: Neural Style Transfer Live
**Description**: Optimization process as content and style blend in real-time.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable), TensorFlow.js (for real inference)
- Quality: Polished, production-ready
- Performance: Optimize for interactive speed (may need smaller images)

**Prerequisites for this visualization**:
- User understands CNNs and optimization

**Learning Objectives the visualization must support**:
1. See the content + style → result pipeline
2. Watch output image evolve through optimization
3. Understand content loss vs style loss
4. Explore different content/style combinations

**Required Interactive Features**:

**Image Selection Panel**:
1. **Content Image**:
   - Preset images (landscapes, portraits, objects)
   - Upload custom image
   - Thumbnail preview
2. **Style Image**:
   - Preset styles (Van Gogh, Monet, abstract patterns)
   - Upload custom style
   - Thumbnail preview
3. **Image Dimensions**: Size selector (smaller = faster)

**Three-Panel Display**:
1. **Content Panel**: Original content image
2. **Style Panel**: Style reference image
3. **Output Panel**: Evolving stylized result (main focus)
4. **Layout Options**: Side-by-side or triangular arrangement

**Optimization Controls**:
1. **Start/Pause**: Begin or pause optimization
2. **Iteration Counter**: Current step number
3. **Speed Control**: Steps per display update
4. **Reset**: Return to initial state
5. **Max Iterations**: Slider (100-1000)

**Loss Display**:
1. **Content Loss Curve**: Plot over iterations
2. **Style Loss Curve**: Plot over iterations
3. **Total Loss Curve**: Combined loss
4. **Current Values**: Numeric display

**Parameter Controls**:
1. **Content Weight (α)**: Slider
2. **Style Weight (β)**: Slider
3. **Content Layer Selector**: Which VGG layer for content
4. **Style Layers Selector**: Which layers for style
5. **Learning Rate**: Optimization step size

**Feature Visualization** (optional advanced):
1. **Content Features**: Show activations for content
2. **Style Gram Matrices**: Visualize style correlations
3. **Layer-by-Layer Contribution**: How each layer affects result

**History Playback**:
1. **Checkpoint Storage**: Save output at intervals
2. **Playback Slider**: Scrub through optimization history
3. **Animation Mode**: Auto-play evolution
4. **Export Result**: Save final image

**Visual Design Requirements**:
- Large, clear output image display
- Smooth image updates during optimization
- Clean loss curve rendering
- Intuitive before/after comparison
- Professional image frame styling

**Code Architecture Requirements**:
- TensorFlow.js with VGG19 for feature extraction
- Gram matrix computation
- Custom optimization loop (or tf.train.Optimizer)
- Image preprocessing/postprocessing
- Checkpoint management

**Deliverables**:
Complete TypeScript implementation with image selection, live optimization visualization, loss tracking, and parameter controls.
```

---

## H2: Spiking Neural Network

### H2 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Spiking Neural Networks — Biological Inspiration and Neuromorphic Computing

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see temporal spike propagation dynamics, introducing them to neuromorphic computing concepts.

**Prerequisites the learner should already understand**:
- Basic neural network concepts (C1)
- What biological neurons do (very basic)
- Time-based vs static processing

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand how SNNs differ from traditional ANNs
2. Know the leaky integrate-and-fire neuron model
3. Understand spikes as discrete events in time
4. See the potential advantages (efficiency, temporal data)
5. Know about neuromorphic hardware

**Required Sections**:
1. **Traditional ANNs vs SNNs**:
   - ANNs: continuous activations, one forward pass
   - SNNs: discrete spikes over time, temporal dynamics
2. **Biological Inspiration**:
   - Real neurons communicate via action potentials (spikes)
   - Spike timing matters
   - Energy efficient (neurons fire sparsely)
3. **Leaky Integrate-and-Fire (LIF) Neuron**:
   - Membrane potential accumulates input
   - "Leaks" over time (decays)
   - Fires spike when threshold reached
   - Resets after firing (refractory period)
4. **Spike Encoding**:
   - Rate coding: frequency of spikes = intensity
   - Temporal coding: timing of spikes carries information
   - Population coding: patterns across neurons
5. **Spike Propagation**:
   - Input spikes affect downstream neurons
   - Temporal patterns propagate through network
   - Timing-dependent effects
6. **Training SNNs**:
   - STDP: Spike-Timing Dependent Plasticity
   - Surrogate gradients for backprop
   - Still an active research area
7. **Neuromorphic Hardware**:
   - Intel Loihi, IBM TrueNorth
   - Extremely energy efficient
   - Good for edge devices, always-on sensing
8. **Why This Matters for ML/AI**:
   - Alternative paradigm to current deep learning
   - Potential for massive efficiency gains
   - Better for temporal/event-based data
   - Growing research interest

**Tone**: Emphasize the biological connection and future potential. Make spikes feel dynamic and alive.

**Length**: Approximately 1700-2100 words introducing this alternative paradigm clearly.
```

### H2 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: H2
**Title**: Spiking Neural Network
**Description**: Temporal spike propagation dynamics. Neuromorphic computing intro.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target with many neurons

**Prerequisites for this visualization**:
- User understands basic neural network concepts

**Learning Objectives the visualization must support**:
1. See neurons as temporal processing units
2. Watch membrane potential rise, spike, and reset
3. See spikes propagate through layers
4. Understand the temporal dimension

**Required Interactive Features**:

**Network Display**:
1. **3D Neuron Layout**: Neurons as spheres in layers
2. **Connection Lines**: Synapses between neurons
3. **Spike Animation**: Visual flash/pulse when neuron fires
4. **Spike Propagation**: Animated signals along connections

**Single Neuron View**:
1. **LIF Neuron Diagram**: Detailed view of one neuron
2. **Membrane Potential Plot**: Real-time voltage trace
3. **Threshold Line**: Horizontal line showing firing threshold
4. **Spike Markers**: Vertical lines when spikes occur
5. **Decay Visualization**: Show potential leaking down

**Time Controls**:
1. **Time Slider**: Scrub through simulation
2. **Play/Pause**: Run simulation
3. **Speed Control**: Slow motion to fast forward
4. **Step Mode**: Advance by single timestep
5. **Time Display**: Current simulation time

**Input Control**:
1. **Input Spike Pattern**: Define input spike times
2. **Preset Patterns**:
   - Regular train (constant frequency)
   - Burst (rapid spikes then pause)
   - Random Poisson
3. **Input Rate Slider**: Average firing rate
4. **Manual Trigger**: Click to inject spike

**Neuron Parameters**:
1. **Threshold Slider**: Firing threshold voltage
2. **Leak Rate Slider**: How fast potential decays
3. **Refractory Period**: Time after spike before can fire again
4. **Synaptic Weight Slider**: Connection strength

**Network Simulation**:
1. **Layer Configuration**: Input → Hidden → Output
2. **Watch Propagation**: See spikes travel through layers
3. **Population Activity**: Raster plot of all neurons
4. **Firing Rate Display**: Spikes per second for each neuron

**Encoding Demonstration**:
1. **Rate Coding Mode**: Input intensity → spike frequency
2. **Image to Spikes**: Convert image pixels to spike rates
3. **Output Decoding**: How to read output spikes

**Visual Design Requirements**:
- Dynamic, pulsing neuron animations
- Spike trails along connections
- Real-time membrane potential plots
- Color coding for neuron state (resting, rising, firing, refractory)
- Smooth time-based animations

**Code Architecture Requirements**:
- LIF neuron class with update method
- Network simulation loop
- Spike event management
- Time-series data storage for plots
- Efficient many-neuron rendering

**Deliverables**:
Complete TypeScript implementation with LIF neurons, spike propagation visualization, membrane potential plots, and temporal controls.
```

---

## H3: Ensemble Voting Visualiser

### H3 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Ensemble Methods — Combining Multiple Models

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see multiple models making predictions with votes combining visually to produce ensemble predictions.

**Prerequisites the learner should already understand**:
- Classification basics
- What different model types are (trees, neural nets, etc.)
- Probability and confidence

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand ensemble methods combine multiple models
2. Know different voting schemes (hard voting, soft voting, weighted)
3. Understand why ensembles often outperform single models
4. Know common ensemble methods (bagging, boosting, stacking)
5. See the bias-variance perspective on ensembles

**Required Sections**:
1. **The Wisdom of Crowds** — Multiple opinions often better than one
2. **Why Ensembles Work**:
   - Different models make different errors
   - Errors cancel out on average
   - Reduces variance while maintaining low bias
3. **Voting Schemes**:
   - Hard voting: majority class wins
   - Soft voting: average probabilities, then decide
   - Weighted voting: some models count more
4. **Types of Ensembles**:
   - Bagging (Random Forest): parallel, independent models
   - Boosting (XGBoost, AdaBoost): sequential, focus on errors
   - Stacking: models feed into meta-model
5. **Diversity is Key**:
   - Ensemble of identical models = single model
   - Need models that disagree (on different samples)
   - Different algorithms, different data subsets
6. **Bias-Variance View**:
   - Bagging reduces variance (averaging stabilizes)
   - Boosting reduces bias (focusing on errors)
7. **Practical Considerations**:
   - More compute at inference time
   - Harder to interpret
   - Usually worth it for important predictions
8. **Why This Matters for ML/AI**:
   - Ensembles win competitions (Kaggle)
   - Production systems often use ensembles
   - Random Forest is based on ensemble principles

**Tone**: Use the voting/democracy metaphor heavily. Make combination feel democratic and intuitive.

**Length**: Approximately 1500-1900 words with clear ensemble type explanations.
```

### H3 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: H3
**Title**: Ensemble Voting Visualiser
**Description**: Multiple models making predictions with visual votes combining.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands classification

**Learning Objectives the visualization must support**:
1. See individual model predictions
2. Watch votes aggregate into ensemble prediction
3. Compare voting schemes
4. Understand how diversity helps

**Required Interactive Features**:

**Model Panel**:
1. **Model Icons**: Visual representation of each model (3-7 models)
2. **Model Types**: Different shapes/colors for different model types
3. **Model Names**: Labels (Model 1, Model 2, or type names)
4. **Individual Predictions**: Each model shows its prediction

**Input Display**:
1. **Current Sample**: Show the input being classified
2. **Sample Selector**: Choose different test samples
3. **Feature Display**: Show input features visually
4. **True Label**: Ground truth (for comparison)

**Voting Visualization**:
1. **Vote Casting Animation**: Votes fly from models to ballot box
2. **Vote Counters**: Tally for each class
3. **Probability Bars**: For soft voting, show probability contributions
4. **Winner Highlight**: Final ensemble prediction

**Voting Scheme Toggle**:
1. **Hard Voting**: Each model casts one vote
2. **Soft Voting**: Models contribute probability distributions
3. **Weighted Voting**: Some models have more influence
4. **Scheme Comparison**: Side-by-side results

**Weight Controls** (for weighted voting):
1. **Weight Sliders**: Adjust each model's weight
2. **Auto-Weight**: Button to set weights by validation accuracy
3. **Weight Display**: Visual size of model's influence

**Agreement Analysis**:
1. **Agreement Meter**: How much models agree
2. **Disagreement Highlighting**: Show where models differ
3. **Confidence Indicator**: Ensemble certainty

**Accuracy Comparison**:
1. **Individual Accuracy**: Each model's performance
2. **Ensemble Accuracy**: Combined performance
3. **Improvement Indicator**: Show ensemble > individuals

**Decision Boundary View** (for 2D data):
1. **Individual Boundaries**: Each model's boundary
2. **Ensemble Boundary**: Combined decision boundary
3. **Overlay Mode**: See all boundaries together
4. **Voting Regions**: Where models agree/disagree

**Visual Design Requirements**:
- Distinct icons for each model
- Animated vote transfer
- Clear tally displays
- Color-coded by class prediction
- Professional ballot box metaphor

**Code Architecture Requirements**:
- Mock model predictions (or simple real models)
- Voting aggregation functions
- Animation sequencing for votes
- Multiple visualization modes
- Accuracy tracking

**Deliverables**:
Complete TypeScript implementation with model display, animated voting, scheme comparison, and accuracy analysis.
```

---

## H4: Knowledge Distillation

### H4 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Knowledge Distillation — Teaching a Small Model from a Large One

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see the teacher → student knowledge transfer process visualized.

**Prerequisites the learner should already understand**:
- Neural network training (C1, C2)
- Softmax and probabilities (C6)
- What model size/complexity means

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the motivation (deploy small, train large)
2. Know the teacher-student framework
3. Understand soft labels vs hard labels
4. See how temperature affects softmax
5. Know the distillation loss

**Required Sections**:
1. **The Problem** — Large models are accurate but expensive to deploy
2. **The Idea** — Train small model to mimic large model's behavior
3. **Teacher and Student**:
   - Teacher: large, accurate, pre-trained model
   - Student: small, fast, to be trained
   - Goal: student learns to predict like teacher
4. **Why Not Just Train Small Model on Data?**:
   - Hard labels (0/1) lose information
   - Teacher's soft outputs capture more: "It's 70% cat, 25% dog, 5% tiger"
   - Soft labels provide richer supervision
5. **Temperature in Softmax**:
   - Higher temperature → softer distribution
   - Reveals "dark knowledge" in small probabilities
   - Teacher and student use same temperature
6. **Distillation Loss**:
   - Match student's soft outputs to teacher's soft outputs
   - Often combined with standard hard label loss
   - Loss = α × soft_loss + (1-α) × hard_loss
7. **What Gets Transferred**:
   - Relative probabilities between classes
   - Inter-class relationships
   - Teacher's mistakes also teach (what NOT to predict)
8. **Why This Matters for ML/AI**:
   - Deploy BERT-like quality on mobile
   - Edge inference with limited compute
   - Foundation of many efficient model techniques

**Tone**: Emphasize the "teaching" metaphor. Make knowledge transfer feel intuitive.

**Length**: Approximately 1600-2000 words with clear pipeline explanation.
```

### H4 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: H4
**Title**: Knowledge Distillation
**Description**: Teacher → student knowledge transfer visualised.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands neural networks and softmax

**Learning Objectives the visualization must support**:
1. See teacher and student as separate networks
2. Watch soft labels transfer from teacher to student
3. Understand temperature effect on softmax
4. See student gradually match teacher

**Required Interactive Features**:

**Network Display**:
1. **Teacher Network**: Large network visualization (many layers/neurons)
2. **Student Network**: Small network visualization (fewer layers/neurons)
3. **Size Comparison**: Visual scale difference
4. **Labels**: Clear "Teacher" and "Student" labels

**Input Flow**:
1. **Sample Input**: Image or data point
2. **Input to Both**: Same input goes to teacher and student
3. **Flow Animation**: Data flowing through networks

**Soft Label Visualization**:
1. **Teacher Output**: Probability distribution (bar chart)
2. **Student Output**: Probability distribution (bar chart)
3. **Side-by-Side Comparison**: Show distributions together
4. **Match Indicator**: How close student is to teacher

**Temperature Control**:
1. **Temperature Slider**: τ from 1 to 20
2. **Effect on Teacher Output**: Watch distribution soften
3. **Effect on Student Target**: Same temperature applied
4. **Comparison**: τ=1 vs higher τ outputs

**Distillation Training**:
1. **Train Button**: Start student training
2. **Epoch Counter**: Training progress
3. **Soft Loss Display**: KL divergence from teacher
4. **Hard Loss Display**: Cross-entropy from true labels
5. **Total Loss**: Weighted combination

**Training Animation**:
1. **Knowledge Flow**: Visual "knowledge" flowing from teacher to student
2. **Student Weights Updating**: Indicate learning
3. **Output Matching**: Watch student distribution approach teacher
4. **Progress Bar**: Overall training completion

**Before/After Comparison**:
1. **Untrained Student**: Random outputs
2. **Trained Student**: Matches teacher
3. **Test Samples**: Multiple samples to verify

**Accuracy Panel**:
1. **Teacher Accuracy**: Reference performance
2. **Student Accuracy**: After distillation
3. **Student Size**: Parameter count comparison
4. **Speed Comparison**: Inference time ratio

**Visual Design Requirements**:
- Clear size difference between networks
- Animated knowledge transfer effect
- Smooth distribution bar charts
- Temperature effect clearly visible
- Professional teacher/student metaphor

**Code Architecture Requirements**:
- Teacher model (pretrained or simulated)
- Student model (trainable)
- Soft label generation with temperature
- Distillation loss computation
- Training loop visualization

**Deliverables**:
Complete TypeScript implementation with network comparison, soft label visualization, temperature controls, and training animation.
```

---

## Summary

| ID | Title | Education Prompt | Visualization Prompt |
|----|-------|------------------|---------------------|
| H1 | Neural Style Transfer Live | ✅ | ✅ |
| H2 | Spiking Neural Network | ✅ | ✅ |
| H3 | Ensemble Voting Visualiser | ✅ | ✅ |
| H4 | Knowledge Distillation | ✅ | ✅ |
