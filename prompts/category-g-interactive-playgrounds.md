# Category G: Interactive Playgrounds — LLM Prompts

> **Target Audience**: Software developers with limited mathematics background  
> **Tech Stack**: Three.js, TypeScript, TensorFlow.js (where applicable)  
> **Complexity**: Polished, production-quality code  
> **Purpose**: Educational portfolio demonstrating ML/AI concepts visually

---

## G1: Perceptron Playground

### G1 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Perceptron — The Simplest Neural Network

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will drag points around and watch a perceptron find the separating hyperplane, also learning about its linear limitations.

**Prerequisites the learner should already understand**:
- Coordinates and points in 2D
- What a line equation is (ax + by + c = 0)
- Basic idea of classification

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the perceptron as a binary linear classifier
2. Know the perceptron algorithm (classify, check, update)
3. Visualize the decision boundary as a line
4. Understand linear separability
5. Know the XOR problem (why perceptrons have limits)

**Required Sections**:
1. **Historical Context** — Rosenblatt's perceptron (1958), excitement, then AI winter
2. **The Perceptron Model**:
   - Inputs × weights + bias
   - Sum = weighted combination
   - Activation: sign function (output +1 or -1)
   - Formula: y = sign(w·x + b)
3. **The Decision Boundary**:
   - Where w·x + b = 0
   - A line (or hyperplane in higher dimensions)
   - Points on one side = class A, other side = class B
4. **The Learning Algorithm**:
   - Initialize weights randomly
   - For each point: classify, check if correct
   - If wrong: update weights toward correct answer
   - Repeat until all points correct (if linearly separable)
5. **Linear Separability**:
   - Some datasets can be separated by a line
   - Perceptron guaranteed to converge for these
   - But some datasets CANNOT be linearly separated
6. **The XOR Problem**:
   - XOR: (0,0)→0, (0,1)→1, (1,0)→1, (1,1)→0
   - No line can separate these classes
   - Famous limitation that led to multi-layer networks
7. **Why This Matters for ML/AI**:
   - Foundation for understanding neural networks
   - Shows why we need multiple layers
   - The learning algorithm is gradient-free but inspired gradient descent

**Tone**: Historical but practical. Make the limitations feel like a cliffhanger leading to deep learning.

**Length**: Approximately 1600-2000 words with clear XOR explanation.
```

### G1 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: G1
**Title**: Perceptron Playground
**Description**: Drag points, watch perceptron find separating hyperplane. Show linear limits.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic 2D coordinates

**Learning Objectives the visualization must support**:
1. Create datasets by placing points
2. Watch perceptron learn to separate classes
3. See the decision boundary update
4. Discover XOR limitation interactively

**Required Interactive Features**:

**Data Canvas**:
1. **2D Plane**: Coordinate grid for placing points
2. **Add Points**: Click to place points
3. **Class Selection**: Toggle between class A (blue) and class B (red)
4. **Drag Points**: Move existing points to new positions
5. **Delete Points**: Right-click or button to remove
6. **Clear All**: Reset canvas

**Perceptron Visualization**:
1. **Decision Boundary Line**: Shows current w·x + b = 0
2. **Boundary Animation**: Smooth updates as weights change
3. **Positive/Negative Regions**: Background shading for each class
4. **Weight Vector Arrow**: Optional display of w vector

**Training Controls**:
1. **Train Button**: Run perceptron algorithm
2. **Step Mode**: One update at a time
3. **Speed Control**: Fast/slow training animation
4. **Current Step Display**: "Training: epoch 3, point 5"
5. **Reset Weights**: Reinitialize randomly

**Learning Visualization**:
1. **Current Point Highlight**: Show which point is being checked
2. **Correct/Wrong Indicator**: Green/red flash on classification
3. **Weight Update Animation**: Show weight vector shifting
4. **Convergence Indicator**: "Converged!" when all correct

**Preset Datasets**:
1. **Linearly Separable**: Easy dataset
2. **XOR Pattern**: Four points in XOR configuration
3. **Almost Separable**: One outlier
4. **Random Clusters**: Random linearly separable data

**XOR Demonstration**:
1. **XOR Preset Button**: Load XOR points automatically
2. **Failure Mode**: Watch perceptron oscillate without converging
3. **Iteration Counter**: Show it trying forever
4. **Explanation Popup**: Why this fails

**Neuron Diagram** (side panel):
1. **Visual Neuron**: Inputs, weights, sum, activation
2. **Current Values**: Live weight and bias values
3. **Output**: Current classification

**Visual Design Requirements**:
- Clean grid background
- Distinct class colors (blue/red)
- Smooth line animation
- Point selection highlight
- Clear region coloring

**Code Architecture Requirements**:
- Perceptron class with update method
- Point management (add, remove, drag)
- Decision boundary calculation
- Step-by-step training mode
- Convergence detection

**Deliverables**:
Complete TypeScript implementation with point manipulation, perceptron training, XOR demo, and visual neuron diagram.
```

---

## G2: Embedding Space Explorer

### G2 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Embedding Spaces — Representing Words and Images as Vectors

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will explore word2vec/image embeddings in 3D using t-SNE/UMAP, searching and discovering relationships.

**Prerequisites the learner should already understand**:
- Vectors as points in space (A1)
- Dot products as similarity (A1)
- Neural network basics (C1)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand embeddings as learned vector representations
2. Know that similar items have nearby vectors
3. Understand dimensionality reduction (t-SNE, UMAP) for visualization
4. See famous examples (king - man + woman = queen)
5. Know applications of embeddings

**Required Sections**:
1. **What is an Embedding?** — Converting discrete items (words, images) to continuous vectors
2. **Why Embeddings?**:
   - Neural networks need numbers
   - One-hot encoding is sparse and meaningless
   - Embeddings capture semantic meaning
3. **Word Embeddings (word2vec)**:
   - Words → 100-300 dimensional vectors
   - Similar words = nearby vectors
   - Famous: king - man + woman ≈ queen
   - Trained on word co-occurrence
4. **Image Embeddings**:
   - Images → feature vectors
   - Similar images = nearby vectors
   - From CNN layers or dedicated embedding models
5. **The High-Dimensional Challenge**:
   - Embeddings have 100s of dimensions
   - Can't visualize directly
   - Need dimensionality reduction
6. **t-SNE and UMAP**:
   - Reduce to 2D or 3D for visualization
   - Preserve local neighborhood structure
   - Similar items stay close
   - Different items pushed apart
7. **Exploring Embedding Space**:
   - Clusters = semantic groups
   - Directions = semantic relationships
   - Arithmetic = analogy completion
8. **Why This Matters for ML/AI**:
   - Embeddings everywhere: NLP, vision, recommender systems
   - Foundation for transformers and LLMs
   - Understanding embeddings = understanding modern AI

**Tone**: Focus on the "meaning as position" insight. Make semantic space feel tangible.

**Length**: Approximately 1800-2200 words with concrete examples and analogies.
```

### G2 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: G2
**Title**: Embedding Space Explorer
**Description**: word2vec/image embeddings in 3D with t-SNE/UMAP. Search and explore relationships.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands vectors as positions

**Learning Objectives the visualization must support**:
1. See items as points in 3D space
2. Discover clusters of similar items
3. Explore relationships via search
4. Try vector arithmetic (analogies)

**Required Interactive Features**:

**3D Space View**:
1. **Point Cloud**: Hundreds/thousands of embedded items
2. **Camera Controls**: Orbit, pan, zoom
3. **Point Labels**: Show label on hover
4. **Point Colors**: Color by category/cluster
5. **Cluster Highlighting**: Visual cluster boundaries

**Dataset Options**:
1. **Word Embeddings**: Common English words (500-2000)
2. **Country Embeddings**: Countries with geographic/economic clusters
3. **MNIST Digits**: Handwritten digit images
4. **Custom Upload**: Load own embeddings (JSON format)

**Search and Select**:
1. **Search Box**: Type to find specific items
2. **Search Results**: Dropdown of matches
3. **Jump to Item**: Center view on searched item
4. **Multi-Select**: Select multiple items
5. **Selected Panel**: Show selected items list

**Nearest Neighbors**:
1. **Select Point**: Click to select
2. **Show Neighbors**: Highlight N nearest neighbors
3. **Neighbor Count Slider**: How many neighbors to show
4. **Connection Lines**: Draw lines to neighbors
5. **Similarity Scores**: Show distances/similarities

**Vector Arithmetic** (analogy mode):
1. **Formula Builder**: "A - B + C = ?"
2. **Select Items**: Click to fill A, B, C slots
3. **Compute Result**: Find nearest point to result vector
4. **Famous Examples**: Preset king-man+woman=queen
5. **Visualize Operation**: Show vectors being added/subtracted

**Dimensionality Reduction Display**:
1. **Algorithm Toggle**: t-SNE vs UMAP
2. **Perplexity/Neighbors Slider**: Algorithm parameters
3. **Re-compute Button**: Recalculate projection
4. **Original Dimension Info**: Show true embedding dimension

**Cluster Analysis**:
1. **Auto-Cluster**: K-means or similar
2. **Cluster Colors**: Each cluster distinct color
3. **Cluster Labels**: Inferred or manual labels
4. **Inter-Cluster Distance**: Show relationships between clusters

**Visual Design Requirements**:
- Dense but navigable point cloud
- Readable labels on hover
- Smooth camera transitions
- Clear selection highlighting
- Intuitive analogy interface

**Code Architecture Requirements**:
- Embedding data loading/parsing
- Efficient point cloud rendering (BufferGeometry)
- Spatial index for nearest neighbor queries
- Vector arithmetic utilities
- Camera and interaction management

**Deliverables**:
Complete TypeScript implementation with 3D exploration, search, nearest neighbors, and vector arithmetic interface.
```

---

## G3: GAN Training Dance

### G3 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Generative Adversarial Networks — The Generator vs Discriminator Game

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will watch the generator vs discriminator loss tug-of-war and see generated outputs evolving over training.

**Prerequisites the learner should already understand**:
- Neural network basics (C1)
- Loss functions (C5)
- What generative models do (create new data)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the adversarial game between Generator and Discriminator
2. Know what each network's role is
3. See how the training dynamics work
4. Understand mode collapse and training instability
5. Know applications of GANs

**Required Sections**:
1. **The Generative Goal** — Create new data that looks like real data
2. **The Two Players**:
   - Generator (G): Creates fake samples from noise
   - Discriminator (D): Classifies real vs fake
3. **The Adversarial Game**:
   - D wants to correctly identify fakes
   - G wants to fool D
   - Each improves in response to the other
4. **Training Loop**:
   - Train D: show real (label 1) and fake (label 0)
   - Train G: generate, get D's opinion, improve to fool D
   - Alternate between D and G updates
5. **Loss Dynamics**:
   - D loss: how well it discriminates
   - G loss: how well it fools D
   - Ideally both hover around equilibrium
   - Seesaw pattern is normal
6. **Training Challenges**:
   - Mode collapse: G only produces one type of output
   - Training instability: one player dominates
   - Vanishing gradients when D is too strong
7. **Evolution of Outputs**:
   - Start: random noise
   - Middle: blurry, partial features
   - End: realistic outputs
8. **Why This Matters for ML/AI**:
   - GANs create realistic images, video, audio
   - Foundation for DALL-E, image editing, deepfakes
   - Adversarial training used beyond generation

**Tone**: Emphasize the game/competition metaphor. Make the training dynamics feel like a rivalry.

**Length**: Approximately 1700-2100 words with clear stage descriptions.
```

### G3 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: G3
**Title**: GAN Training Dance
**Description**: Generator vs discriminator loss tug-of-war, generated outputs evolving.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable), TensorFlow.js (optional for real training)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands neural networks and loss functions

**Learning Objectives the visualization must support**:
1. See the two-player game visually
2. Watch loss curves evolve with seesaw pattern
3. See generated outputs improve over time
4. Understand training dynamics

**Required Interactive Features**:

**Architecture View**:
1. **Two Network Boxes**: Generator and Discriminator
2. **Data Flow**:
   - Noise → Generator → Fake Image
   - Real Image → Discriminator → Real/Fake score
   - Fake Image → Discriminator → Real/Fake score
3. **Connection Arrows**: Showing data paths
4. **Current Phase Indicator**: "Training Generator" or "Training Discriminator"

**Loss Curves**:
1. **Dual Plot**: G loss and D loss over time
2. **Real-Time Update**: Curves grow during training
3. **Ideal Region**: Show balanced loss zone
4. **Anomaly Indicators**: Highlight mode collapse or divergence
5. **Legend**: Clear G vs D labels

**Generated Output Gallery**:
1. **Output Grid**: 4x4 or similar grid of generated images
2. **Epoch Slider**: Jump to different training stages
3. **Animation Mode**: Watch outputs evolve over training
4. **Quality Indicator**: Rough measure of output quality

**Training Controls**:
1. **Train Button**: Start/pause training
2. **Step Mode**: One training step at a time
3. **Speed Control**: Fast/slow simulation
4. **Reset**: Start from scratch
5. **Epoch Counter**: Current training iteration

**Balance Visualization**:
1. **Tug-of-War Visual**: Two forces pulling (G vs D)
2. **Strength Indicator**: Who's currently winning
3. **Equilibrium Marker**: Ideal balanced state
4. **Seesaw Animation**: Show back-and-forth dynamics

**Mode Collapse Demo**:
1. **Collapse Preset**: Configuration that leads to mode collapse
2. **Output Diversity**: Show all outputs looking the same
3. **Detection Indicator**: Warning when collapse detected
4. **Fix Suggestions**: Techniques to address

**Real Data Comparison**:
1. **Real Samples Panel**: Show actual training data
2. **Side-by-Side**: Compare real vs generated
3. **Similarity Score**: How close generated is to real

**Visual Design Requirements**:
- Clear two-player visual metaphor
- Smooth loss curve rendering
- Image grid with clear boundaries
- Dynamic tug-of-war visualization
- Training phase highlighting

**Code Architecture Requirements**:
- GAN training simulation (or real TF.js training)
- Loss history tracking
- Output storage at checkpoints
- Animation and replay system
- Mode collapse detection heuristics

**Deliverables**:
Complete TypeScript implementation with architecture view, loss dynamics, output evolution, and training controls.
```

---

## G4: Decision Boundary Evolution

### G4 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Decision Boundaries — Watching a Classifier Learn

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will watch classifier boundaries form during training on 2D data.

**Prerequisites the learner should already understand**:
- Classification basics
- Neural networks (C1)
- Gradient descent (D1)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand decision boundaries as classification regions
2. See how boundaries evolve during training
3. Know how model complexity affects boundary shape
4. Recognize underfitting, good fit, and overfitting in boundaries

**Required Sections**:
1. **What is a Decision Boundary?** — The frontier between class regions
2. **Linear Boundaries**:
   - Single line/plane separating classes
   - Logistic regression, perceptron
   - Limited to linearly separable problems
3. **Non-Linear Boundaries**:
   - Neural networks with hidden layers
   - Can curve around data
   - More layers = more complex boundaries
4. **Boundary Evolution**:
   - Start: random boundary (based on initial weights)
   - Training: boundary shifts to reduce errors
   - End: boundary separates classes (hopefully)
5. **Complexity and Capacity**:
   - Simple model: smooth boundaries
   - Complex model: wiggly, detailed boundaries
   - Too complex: overfits, follows noise
6. **Reading Boundaries**:
   - Wide margins = confident regions
   - Narrow regions = uncertain
   - Wisps and tendrils = possible overfitting
7. **Why This Matters for ML/AI**:
   - Visualizing what the model "learned"
   - Debugging classification problems
   - Understanding model capacity

**Tone**: Focus on the visual evolution story. Make training feel like watching a picture develop.

**Length**: Approximately 1400-1700 words with vivid descriptions of boundary evolution.
```

### G4 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: G4
**Title**: Decision Boundary Evolution
**Description**: Watch classifier boundaries form during training on 2D data.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable), TensorFlow.js (for real training)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands classification and neural networks

**Learning Objectives the visualization must support**:
1. See decision boundary form from random start
2. Watch boundary evolve through training
3. Compare simple vs complex model boundaries
4. Identify underfitting and overfitting visually

**Required Interactive Features**:

**Data Canvas**:
1. **2D Scatter Plot**: Training points with class colors
2. **Add Points**: Click to add data
3. **Class Toggle**: Switch between classes when adding
4. **Preset Datasets**:
   - Linear separable
   - Circular/moon shapes
   - XOR pattern
   - Spiral
5. **Clear/Reset**: Remove all points

**Decision Boundary Visualization**:
1. **Background Coloring**: Regions colored by predicted class
2. **Boundary Line**: Explicit boundary contour
3. **Confidence Gradient**: Intensity based on classification confidence
4. **Real-Time Update**: Boundary updates during training

**Model Configuration**:
1. **Architecture Selector**:
   - Logistic regression (linear boundary)
   - 1 hidden layer (simple curves)
   - 2+ hidden layers (complex boundaries)
2. **Neurons per Layer**: Slider
3. **Activation Function**: ReLU, Tanh, Sigmoid

**Training Controls**:
1. **Train Button**: Start/pause training
2. **Epoch Counter**: Current iteration
3. **Step Mode**: One gradient update at a time
4. **Learning Rate Slider**: Adjust during training
5. **Reset Weights**: Reinitialize randomly

**Training Visualization**:
1. **Loss Curve**: Plot loss over epochs
2. **Accuracy Display**: Train/test accuracy
3. **Boundary History**: Ghost of past boundaries
4. **Animation Playback**: Replay training evolution

**Comparison Mode**:
1. **Side-by-Side**: Two models on same data
2. **Simple vs Complex**: Compare capacity effects
3. **Synchronized Training**: Both train simultaneously
4. **Metrics Comparison**: Loss/accuracy for both

**Overfitting Demo**:
1. **Complex Model Preset**: High-capacity network
2. **Watch Boundary Wiggles**: See overfitting develop
3. **Test Point Indicator**: Show generalization failure

**Visual Design Requirements**:
- Smooth boundary rendering (high resolution grid)
- Clear class colors (blue/red/orange)
- Confidence as color intensity
- Ghost boundaries for history
- Clean scatter point display

**Code Architecture Requirements**:
- TensorFlow.js model (configurable architecture)
- Dense grid prediction for boundary rendering
- Training loop with state capture
- History management for playback
- Multi-model comparison support

**Deliverables**:
Complete TypeScript implementation with data creation, real-time training visualization, model comparison, and overfitting demonstration.
```

---

## Summary

| ID | Title | Education Prompt | Visualization Prompt |
|----|-------|------------------|---------------------|
| G1 | Perceptron Playground | ✅ | ✅ |
| G2 | Embedding Space Explorer | ✅ | ✅ |
| G3 | GAN Training Dance | ✅ | ✅ |
| G4 | Decision Boundary Evolution | ✅ | ✅ |
