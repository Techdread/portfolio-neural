# E1: CNN Layer Explorer — Three.js Visualization Prompt

## Visualization ID
E1

## Title
CNN Layer Explorer

## Description
Filters sliding across images, feature maps at each layer, upload custom images.

---

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
