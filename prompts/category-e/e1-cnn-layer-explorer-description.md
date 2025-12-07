# E1: CNN Layer Explorer — Educational Explanation Prompt

## Topic
Convolutional Neural Networks — Understanding CNN Layers

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see filters sliding across images, feature maps at each layer, with the option to upload custom images.

---

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
