# H1: Neural Style Transfer Live — Three.js Visualization Prompt

## Visualization ID
H1

## Title
Neural Style Transfer Live

## Description
Optimization process as content and style blend in real-time.

---

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
