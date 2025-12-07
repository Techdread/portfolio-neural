# A4: Tensor Visualiser — Three.js Visualization Prompt

## Visualization ID
A4

## Title
Tensor Visualiser

## Description
Show scalars → vectors → matrices → 3D+ tensors. Demonstrate reshaping, broadcasting, slicing.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A4
**Title**: Tensor Visualiser
**Description**: Show scalars → vectors → matrices → 3D+ tensors. Demonstrate reshaping, broadcasting, slicing.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands vectors and matrices
- Basic programming array knowledge

**Learning Objectives the visualization must support**:
1. See the dimensional hierarchy of tensors
2. Understand tensor shapes visually
3. Watch reshaping transform tensor structure
4. See broadcasting "stretch" smaller tensors
5. Visualize slicing operations

**Required Interactive Features**:

**Dimension Explorer Tab**:
1. **Rank Slider**: 0 (scalar) → 1 (vector) → 2 (matrix) → 3 (3D tensor) → 4 (animated)
2. **3D Representation**:
   - Scalar: single glowing cube
   - Vector: row of cubes
   - Matrix: grid of cubes
   - 3D Tensor: cube of cubes with transparency
   - 4D: animate through the 4th dimension
3. **Shape Input**: User enters shape (e.g., [2,3,4])
4. **Element Count**: Display total elements

**Reshape Tab**:
1. **Input Tensor**: Display a tensor with numbered elements
2. **Target Shape Input**: Enter new shape
3. **Animate Reshape**: Elements flow from old positions to new
4. **Validation**: Show error if shapes incompatible
5. **Common Presets**: Flatten, add dimension, squeeze

**Broadcasting Tab**:
1. **Tensor A and B Inputs**: Different shapes
2. **Operation Selector**: Add, Multiply, etc.
3. **Visualization**:
   - Show original tensors
   - Animate "stretching" of smaller tensor
   - Show resulting tensor
4. **Broadcasting Rules Display**: Which dimensions stretched

**Slicing Tab**:
1. **Source Tensor**: 3D grid of cubes with values
2. **Slice Input**: Python-style notation (e.g., [:, 0, 1:3])
3. **Highlight Selection**: Selected elements glow
4. **Extract Animation**: Selected elements move to show result

**Visual Design Requirements**:
- Cubes/spheres for tensor elements with value labels
- Color gradients based on value magnitude
- Transparent outer shells for 3D tensors
- Axis labels (dimension 0, 1, 2, etc.)
- Camera controls (orbit, zoom) for 3D exploration

**Code Architecture Requirements**:
- TensorRepresentation class handling any rank
- Smooth interpolation for all animations
- Clear coordinate system mapping
- Modular operation handlers

**Deliverables**:
Complete TypeScript implementation with all tabs functional, smooth animations, and clear value display.
```
