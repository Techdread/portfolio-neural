# Category E: Architecture Visualisations — LLM Prompts

> **Target Audience**: Software developers with limited mathematics background  
> **Tech Stack**: Three.js, TypeScript, TensorFlow.js (where applicable)  
> **Complexity**: Polished, production-quality code  
> **Purpose**: Educational portfolio demonstrating ML/AI concepts visually

---

## E1: CNN Layer Explorer

### E1 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Convolutional Neural Networks — Understanding CNN Layers

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see filters sliding across images, feature maps at each layer, with the option to upload custom images.

**Prerequisites the learner should already understand**:
- Neural network basics (C1)
- Matrix operations (A2)
- What images are as data (pixel grids)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand convolution as a sliding filter operation
2. Know what a filter/kernel detects (edges, patterns)
3. Understand feature maps as filter outputs
4. Know the role of pooling layers
5. See how CNNs build hierarchical features (edges → shapes → objects)

**Required Sections**:
1. **Why CNNs for Images?** — Fully connected networks don't understand spatial structure
2. **The Convolution Operation**:
   - Filter/kernel: small matrix of learnable weights
   - Sliding window across image
   - Element-wise multiply and sum at each position
   - Output: feature map
3. **Filter Intuition**:
   - What filters detect: edges, corners, textures
   - Early layers: simple features
   - Later layers: complex features (eyes, wheels, etc.)
4. **Stride and Padding**:
   - Stride: how far filter moves each step
   - Padding: handling image borders
   - Output size calculation
5. **Multiple Filters = Multiple Feature Maps**:
   - Each filter detects different feature
   - Stack of feature maps = volume
   - 3D thinking: height × width × channels
6. **Pooling Layers**:
   - Max pooling: keep maximum in region
   - Average pooling: keep average
   - Purpose: reduce size, gain invariance
7. **Hierarchical Features**:
   - Layer 1: edges, colors
   - Layer 2: corners, simple shapes
   - Layer 3+: object parts, full objects
8. **Why This Matters for ML/AI**:
   - CNNs revolutionized computer vision
   - Basis for image classification, detection, segmentation
   - Transfer learning uses pretrained CNN features

**Tone**: Highly visual. Describe what would be seen at each layer. Use the filter metaphor throughout.

**Length**: Approximately 2200-2800 words with detailed explanations of each component.
```

### E1 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: E1
**Title**: CNN Layer Explorer
**Description**: Filters sliding across images, feature maps at each layer, upload custom images.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable), TensorFlow.js (for real CNN inference)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic neural network concepts

**Learning Objectives the visualization must support**:
1. See convolution as sliding filter operation
2. Watch filter produce feature map
3. Explore multiple layers of real CNN
4. See hierarchical feature detection

**Required Interactive Features**:

**Image Input**:
1. **Preset Images**: Simple shapes, handwritten digits, natural images
2. **Upload Custom Image**: File input for user images
3. **Image Display**: Current input image prominently shown
4. **Resize/Crop**: Auto-adjust to network input size

**Convolution Animation**:
1. **Filter Visualization**: Show 3×3 or 5×5 filter weights as grid
2. **Sliding Animation**: Watch filter move across image
3. **Multiplication Display**: Show element-wise products
4. **Sum Display**: Show resulting output pixel
5. **Speed Control**: Slow motion to real-time

**Feature Map Display**:
1. **Layer Selector**: Choose which layer to visualize
2. **Feature Map Grid**: All feature maps from selected layer
3. **Filter-to-Map Connection**: Highlight which filter produced which map
4. **Zoom on Map**: Click to expand individual feature map

**3D Network View**:
1. **Layer Stack**: 3D representation of CNN architecture
2. **Volume Visualization**: Each layer as 3D block (H × W × C)
3. **Connection Lines**: Show data flow between layers
4. **Layer Info**: On hover, show layer details

**Filter Gallery**:
1. **Learned Filters**: Display actual filter weights from layer 1
2. **Filter Patterns**: Show what each filter responds to
3. **Classic Filters**: Compare to hand-designed edge detectors (Sobel, etc.)

**Pooling Demonstration**:
1. **Max Pool Animation**: Show 2×2 regions, maximum selected
2. **Before/After**: Feature map size reduction
3. **Toggle Pooling**: See effect of removing pooling

**Layer-by-Layer Tour**:
1. **Auto Tour Button**: Walk through all layers sequentially
2. **Narration Points**: Key insights at each layer
3. **Feature Complexity**: Show features getting more complex

**Visual Design Requirements**:
- Image and feature maps as textured planes
- Filter weights as colored grids
- Smooth sliding animation
- 3D network with clear layer separation
- Responsive to different image sizes

**Code Architecture Requirements**:
- TensorFlow.js model loading (MobileNet or custom small CNN)
- Layer activation extraction
- Texture generation from arrays
- Animation sequencing for convolution
- Image preprocessing utilities

**Deliverables**:
Complete TypeScript implementation with image input, convolution animation, feature map exploration, and 3D network view.
```

---

## E2: Transformer Attention Visualiser

### E2 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Transformer Attention Mechanism

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see attention heads as connection strengths between tokens.

**Prerequisites the learner should already understand**:
- Matrix multiplication (A2)
- Softmax (C6)
- Neural network basics

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the motivation for attention (handling long sequences)
2. Know the Query, Key, Value framework
3. See attention weights as "how much to focus on each token"
4. Understand multi-head attention
5. Know why transformers dominate NLP and beyond

**Required Sections**:
1. **The Problem with Sequences** — RNNs struggle with long-range dependencies
2. **Attention Intuition** — "Look at relevant parts of the input"
3. **Query, Key, Value**:
   - Query: "What am I looking for?"
   - Key: "What do I contain?"
   - Value: "What do I offer?"
   - Analogy: searching a database
4. **The Attention Formula**:
   - Attention(Q, K, V) = softmax(QK^T / √d) × V
   - Similarity = dot product
   - Scale by √d for stable gradients
   - Softmax for weights summing to 1
5. **Self-Attention** — Tokens attending to other tokens in same sequence
6. **Multi-Head Attention**:
   - Multiple attention "perspectives"
   - Each head learns different relationships
   - Heads combined at the end
7. **Position Encoding** — Adding position information (attention is order-agnostic)
8. **Why This Matters for ML/AI**:
   - Transformers power GPT, BERT, and most modern NLP
   - Attention now used in vision (ViT), audio, and more
   - Understanding attention = understanding modern AI

**Tone**: Demystify attention. Use the "looking" and "focusing" metaphors. Make QKV intuitive.

**Length**: Approximately 2000-2500 words with clear QKV explanation and intuition.
```

### E2 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: E2
**Title**: Transformer Attention Visualiser
**Description**: Attention heads as connection strengths between tokens.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands matrix multiplication and softmax

**Learning Objectives the visualization must support**:
1. See tokens as nodes that attend to each other
2. Visualize attention weights as connection strengths
3. Understand Q, K, V computation
4. Compare different attention heads

**Required Interactive Features**:

**Token Display**:
1. **Input Sequence**: Text input (editable)
2. **Token Circles**: Each token as a node
3. **Token Labels**: Display token text
4. **Linear Arrangement**: Tokens in a row or arc

**Attention Visualization**:
1. **Connection Lines**: Lines between all token pairs
2. **Line Thickness**: Proportional to attention weight
3. **Line Color**: Gradient based on weight strength
4. **Hover Highlight**: Hover on token to emphasize its attention pattern
5. **Click Focus**: Click token to show only its outgoing attention

**Attention Matrix View**:
1. **2D Heatmap**: Tokens × Tokens matrix
2. **Cell Colors**: Attention weight intensity
3. **Row/Column Highlighting**: Synchronized with token selection
4. **Numeric Values**: Show exact weights on hover

**QKV Breakdown**:
1. **Step 1**: Show Q vectors for each token
2. **Step 2**: Show K vectors for each token
3. **Step 3**: Show QK^T computation (similarity matrix)
4. **Step 4**: Show softmax application
5. **Step 5**: Show weighted sum of V vectors
6. **Animation**: Step through the process

**Multi-Head View**:
1. **Head Selector**: Tabs or dropdown for different heads
2. **Head Comparison**: Side-by-side attention patterns
3. **Combined View**: Show aggregated attention across heads
4. **Head Specialization**: Label what each head seems to attend to

**Interactive Attention**:
1. **Manual Weight Adjustment**: Drag to change attention weights
2. **See Output Change**: Watch output embeddings update
3. **Reset**: Return to computed attention

**Example Sentences**:
1. **Preset Inputs**: Sentences showing interesting patterns
   - "The cat sat on the mat" (positional)
   - "It was raining so I took an umbrella" (coreference)
2. **Pattern Labels**: Explain what attention patterns mean

**Visual Design Requirements**:
- Clean token display with readable text
- Smooth curved connection lines (bezier)
- Intuitive color scale (cool to warm)
- Clear matrix heatmap
- Responsive layout for different sequence lengths

**Code Architecture Requirements**:
- Tokenizer (simple word-level or character-level)
- Attention computation (mock or real model)
- Connection line rendering with variable thickness
- Matrix heatmap generation
- Multi-head state management

**Deliverables**:
Complete TypeScript implementation with token visualization, attention connections, matrix view, and QKV breakdown.
```

---

## E3: Autoencoder Latent Space Navigator

### E3 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Autoencoders and Latent Space — Compression and Generation

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will fly through a VAE latent space and watch reconstructions morph as they move.

**Prerequisites the learner should already understand**:
- Neural network basics (C1)
- Idea of compression (making data smaller)
- What dimensions mean

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand autoencoders as compression + reconstruction
2. Know encoder, latent space, and decoder roles
3. Understand latent space as compact representation
4. Know what VAE adds (probabilistic, smooth latent space)
5. See how latent interpolation creates smooth transitions

**Required Sections**:
1. **The Compression Idea** — Represent data with fewer numbers
2. **Autoencoder Architecture**:
   - Encoder: input → compressed representation (latent code)
   - Latent space: the "bottleneck"
   - Decoder: latent code → reconstruction
3. **Why a Bottleneck?** — Forces network to learn essential features
4. **Latent Space Meaning**:
   - Each dimension = some learned feature
   - Points nearby = similar inputs
   - Like a compressed coordinate system
5. **Variational Autoencoder (VAE)**:
   - Encoder outputs distribution, not point
   - Sampling from distribution
   - KL divergence regularisation
   - Results in smoother latent space
6. **Latent Interpolation**:
   - Move between points in latent space
   - Reconstructions morph smoothly
   - Generate new data by exploring
7. **Applications**:
   - Data compression
   - Anomaly detection
   - Generative models (create new faces, etc.)
   - Feature learning
8. **Why This Matters for ML/AI**:
   - Foundation for generative models
   - Latent spaces used everywhere (GAN, diffusion)
   - Understanding representation learning

**Tone**: Focus on the "compression" intuition. Make latent space feel like a map you can explore.

**Length**: Approximately 1800-2200 words with emphasis on latent space intuition.
```

### E3 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: E3
**Title**: Autoencoder Latent Space Navigator
**Description**: Fly through VAE latent space, watch reconstructions morph.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable), TensorFlow.js (for real VAE inference)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands neural network basics

**Learning Objectives the visualization must support**:
1. See the encoder-latent-decoder pipeline
2. Navigate through latent space
3. Watch reconstructions change as position changes
4. Understand interpolation between points

**Required Interactive Features**:

**Latent Space View** (2D or 3D projection):
1. **Point Cloud**: Known data points plotted in latent space
2. **Color Coding**: Points colored by class/category
3. **Current Position Marker**: Large marker for current location
4. **Navigation**:
   - Click to jump to location
   - Drag to pan
   - WASD or arrow keys to fly
5. **Zoom**: Mouse wheel or pinch

**Reconstruction Display**:
1. **Live Reconstruction**: Show decoded output at current position
2. **Real-Time Update**: Changes as user moves
3. **Side Panel**: Always visible reconstruction
4. **Resolution**: Clear enough to see details

**Pipeline Visualization**:
1. **Encoder Box**: Visual representation
2. **Latent Point**: Current encoded position
3. **Decoder Box**: Visual representation
4. **Arrows**: Data flow direction

**Interpolation Mode**:
1. **Select Two Points**: Click to set start and end
2. **Interpolation Slider**: Blend between points
3. **Animation Path**: Show line between points in latent space
4. **Morph Animation**: Auto-play interpolation
5. **Reconstruction Sequence**: Show frames along path

**Dataset Options**:
1. **MNIST Digits**: Classic VAE demo
2. **Fashion MNIST**: Clothing items
3. **Simple Shapes**: Geometric primitives
4. **Preset Exploration Points**: Interesting locations labeled

**Latent Dimension Explorer**:
1. **Dimension Sliders**: Adjust each latent dimension independently
2. **See Effect**: Watch how each dimension affects reconstruction
3. **Dimension Meaning**: Label what each dimension seems to control (if discoverable)

**Generate New Samples**:
1. **Random Point Button**: Jump to random latent location
2. **Gaussian Sample**: Sample from learned prior
3. **Novel Generation**: Show outputs that aren't in training data

**Visual Design Requirements**:
- Smooth point cloud rendering
- Clear reconstruction display
- Intuitive navigation controls
- Path visualization for interpolation
- Class color legend

**Code Architecture Requirements**:
- TensorFlow.js VAE model (pretrained)
- Latent space scatter plot (Three.js points)
- Real-time decoder inference
- Interpolation computation
- Camera controls for navigation

**Deliverables**:
Complete TypeScript implementation with latent space navigation, live reconstruction, and interpolation features.
```

---

## E4: RNN/LSTM Unrolled

### E4 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Recurrent Neural Networks and LSTM — Processing Sequences

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see temporal unrolling, hidden state persistence, and gate operations in LSTMs.

**Prerequisites the learner should already understand**:
- Neural network basics (C1)
- What sequences are (text, time series)
- Backpropagation basics (C2)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand RNNs as networks with memory
2. Know what "unrolling" means
3. Understand hidden state as carried information
4. Know the vanishing gradient problem in RNNs
5. Understand LSTM gates and cell state

**Required Sections**:
1. **The Sequence Problem** — Previous inputs affect current output
2. **RNN Core Idea**:
   - Process one timestep at a time
   - Hidden state passes information forward
   - Same weights used at each timestep
3. **Unrolling Through Time**:
   - Visualize RNN as copies at each timestep
   - Connections between timesteps via hidden state
   - Backprop through time (BPTT)
4. **Hidden State as Memory**:
   - Accumulates information from past
   - Compressed representation of history
   - Gets updated at each step
5. **The Vanishing Gradient Problem**:
   - Gradients shrink through many timesteps
   - Hard to learn long-range dependencies
   - Why standard RNNs struggle with long sequences
6. **LSTM Solution**:
   - Cell state: highway for information
   - Gates control information flow
   - Forget gate: what to discard
   - Input gate: what new information to add
   - Output gate: what to output
7. **Gate Mechanics**:
   - Sigmoid for gate values (0-1)
   - Element-wise multiplication to allow/block
   - Learn when to remember and forget
8. **Why This Matters for ML/AI**:
   - RNNs/LSTMs for sequence modeling
   - Replaced by transformers in many tasks, but still used
   - Understanding helps with any sequential data

**Tone**: Focus on the "memory" metaphor. Make gates intuitive with "keep/forget" language.

**Length**: Approximately 2000-2500 words covering both RNN and LSTM thoroughly.
```

### E4 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: E4
**Title**: RNN/LSTM Unrolled
**Description**: Show temporal unrolling, hidden state persistence, gate operations.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic neural networks

**Learning Objectives the visualization must support**:
1. See RNN as same cell repeated over time
2. Watch hidden state flow between timesteps
3. Understand LSTM gates visually
4. See information flow through cell state

**Required Interactive Features**:

**Basic RNN View**:
1. **Rolled View**: Single RNN cell with loop arrow (recurrence)
2. **Unroll Button**: Animate unrolling into timeline
3. **Unrolled View**: Copies of cell at each timestep
4. **Hidden State Arrows**: Show h passing between steps

**Sequence Input**:
1. **Input Sequence**: Editable text or numbers
2. **Timestep Markers**: Label each input position
3. **Current Timestep Indicator**: Highlight active step
4. **Step Forward/Back**: Move through sequence

**Hidden State Visualization**:
1. **State Vector Display**: Show hidden state values
2. **State Evolution**: Watch state change through time
3. **Color Coding**: Activation intensity as color
4. **State History**: Trail showing how state evolved

**LSTM Cell View**:
1. **Detailed Cell Diagram**: Show all LSTM components
2. **Gates Labeled**: Forget, Input, Output gates
3. **Cell State Highway**: The C_t line running through
4. **Gate Values**: Show sigmoid outputs (0-1)

**Gate Animation**:
1. **Input Arrives**: Show x_t and h_{t-1} entering
2. **Compute Gates**: Animate gate value computation
3. **Forget Step**: Show cell state being masked
4. **Input Step**: Show new information being added
5. **Output Step**: Show hidden state being computed
6. **Step-by-Step Mode**: One operation at a time

**Gate Interactive Mode**:
1. **Manual Gate Sliders**: Adjust forget, input, output gates
2. **See Effect**: Watch how gates affect information flow
3. **Extreme Values**: Set gates to 0 or 1 to see full block/pass

**Comparison View**:
1. **RNN vs LSTM Toggle**: Switch between architectures
2. **Gradient Flow Overlay**: Show how gradients flow differently
3. **Long Sequence Demo**: See vanishing gradient in RNN

**Visual Design Requirements**:
- Clear cell boundaries
- Smooth animations for unrolling
- Gate values as fill levels or bar heights
- Information flow as animated pulses
- Clean timeline layout for unrolled view

**Code Architecture Requirements**:
- RNN/LSTM cell classes
- State management for timesteps
- Gate computation functions
- Animation sequencing
- Interactive gate control

**Deliverables**:
Complete TypeScript implementation with RNN unrolling, LSTM gate visualization, step-by-step animation, and interactive exploration.
```

---

## Summary

| ID | Title | Education Prompt | Visualization Prompt |
|----|-------|------------------|---------------------|
| E1 | CNN Layer Explorer | ✅ | ✅ |
| E2 | Transformer Attention Visualiser | ✅ | ✅ |
| E3 | Autoencoder Latent Space Navigator | ✅ | ✅ |
| E4 | RNN/LSTM Unrolled | ✅ | ✅ |
