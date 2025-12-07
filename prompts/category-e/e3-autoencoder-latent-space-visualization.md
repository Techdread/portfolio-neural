# E3: Autoencoder Latent Space Navigator — Three.js Visualization Prompt

## Visualization ID
E3

## Title
Autoencoder Latent Space Navigator

## Description
Fly through VAE latent space, watch reconstructions morph.

---

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
