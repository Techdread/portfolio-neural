# Category A: Linear Algebra Fundamentals — LLM Prompts

> **Target Audience**: Software developers with limited mathematics background  
> **Tech Stack**: Three.js, TypeScript, TensorFlow.js (where applicable)  
> **Complexity**: Polished, production-quality code  
> **Purpose**: Educational portfolio demonstrating ML/AI concepts visually

---

## A1: Vector Operations

### A1 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Vector Operations (Addition, Subtraction, Scaling, Dot Products)

**Context**: This is part of an interactive Three.js visualization portfolio teaching neural network mathematics. The learner will see an interactive 2D/3D visualization alongside this explanation.

**Prerequisites the learner should already understand**:
- Basic coordinate systems (x, y, z axes)
- What a number line is
- Basic arithmetic operations

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand what a vector represents (magnitude + direction)
2. Know how to perform vector addition and subtraction geometrically
3. Understand scalar multiplication and its effect on vectors
4. Grasp the dot product as a measure of similarity/alignment
5. Connect these concepts to their use in neural networks (e.g., weighted sums)

**Required Sections**:
1. **Intuitive Introduction** — What is a vector? Use real-world analogies (movement, force, direction)
2. **Vector Addition & Subtraction** — Geometric interpretation (tip-to-tail method), with worked examples
3. **Scalar Multiplication** — Stretching/shrinking vectors, negative scalars flip direction
4. **The Dot Product** — Three interpretations:
   - Algebraic: multiply corresponding components and sum
   - Geometric: projection of one vector onto another
   - Similarity: measuring how "aligned" two vectors are (cos θ)
5. **Why This Matters for ML/AI**:
   - Neurons compute weighted sums (dot products of inputs and weights)
   - Embeddings use dot products to measure similarity
   - Attention mechanisms rely on dot product similarity
6. **Mathematical Notation** — Introduce standard notation (bold letters, arrow notation, component form)
7. **Common Pitfalls** — Mistakes developers often make

**Tone**: Conversational but precise. Use code analogies where helpful (vectors as arrays, dot product as reduce operation). Avoid jargon without explanation.

**Length**: Comprehensive — approximately 1500-2000 words with clear section headings.
```

### A1 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A1
**Title**: Vector Operations Visualizer
**Description**: Visualize vector addition, subtraction, scaling, and dot products in 2D/3D. Show dot product as similarity/angle measurement.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target
- Responsive: Desktop-first, but handle window resizing

**Prerequisites for this visualization**:
- User understands basic coordinate systems
- Part of a larger portfolio (consistent styling needed)

**Learning Objectives the visualization must support**:
1. See vectors as arrows with magnitude and direction
2. Watch vector addition happen step-by-step (tip-to-tail)
3. Observe scalar multiplication stretching/shrinking vectors
4. Understand dot product through angle visualization

**Required Interactive Features**:
1. **Mode Selector**: Toggle between 2D and 3D views
2. **Operation Tabs**: Addition, Subtraction, Scaling, Dot Product
3. **Draggable Vectors**: Click and drag to modify vector components
4. **Animation Controls**: Play/pause/step-through for operations
5. **Numeric Display**: Show vector components and results in real-time
6. **Dot Product Mode Specifics**:
   - Show angle between vectors with arc
   - Display cosine value
   - Color gradient indicating similarity (green = aligned, red = perpendicular/opposite)
7. **Grid & Axes**: Clear reference grid with labeled axes
8. **Reset Button**: Return to default vector positions

**Visual Design Requirements**:
- Clean, modern aesthetic (dark background recommended for contrast)
- Distinct colors for Vector A, Vector B, Result Vector
- Smooth animations (eased transitions, not instant)
- Labels on vectors showing their names and component values
- Subtle glow effects on vectors for visibility

**Code Architecture Requirements**:
- Modular structure (separate files for scene setup, vector rendering, UI controls)
- Clear TypeScript interfaces for Vector types
- Event-driven updates (state changes trigger re-renders)
- Well-commented code explaining mathematical operations
- Reusable components that could work for other linear algebra visualizations

**Deliverables**:
1. Main visualization TypeScript file
2. Supporting module files
3. HTML template with required containers
4. CSS for UI controls
5. README with setup instructions

Provide complete, runnable code with all imports and dependencies specified.
```

---

## A2: Matrix Multiplication

### A2 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Matrix Multiplication

**Context**: This is part of an interactive Three.js visualization portfolio teaching neural network mathematics. The learner will see an interactive visualization showing row-by-column multiplication step-by-step and matrices transforming space.

**Prerequisites the learner should already understand**:
- Vectors and vector operations (covered in A1)
- Basic 2D coordinate systems
- Arrays and nested arrays in programming

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand what a matrix represents (a collection of vectors, a transformation, a lookup table)
2. Know the row-by-column rule for matrix multiplication
3. Understand why matrix multiplication order matters (AB ≠ BA)
4. Visualize matrices as transformations of space (rotation, scaling, shearing)
5. Connect matrix multiplication to neural network forward passes

**Required Sections**:
1. **What is a Matrix?** — Think of it as:
   - A table of numbers
   - A collection of row vectors or column vectors
   - A function that transforms inputs to outputs
2. **Matrix Dimensions** — Rows × Columns notation, compatibility rules
3. **The Row-by-Column Algorithm** — Step-by-step with small concrete example (2×3 times 3×2)
4. **Why Order Matters** — AB ≠ BA with geometric intuition (rotate then scale vs scale then rotate)
5. **Matrices as Transformations** — Visual examples:
   - Identity matrix (do nothing)
   - Scaling matrix (stretch/shrink)
   - Rotation matrix (rotate space)
   - Shear matrix (skew space)
6. **Why This Matters for ML/AI**:
   - Neural network layers are matrix multiplications
   - Weight matrices transform activations
   - Batch processing: multiply many inputs at once
   - Understanding shapes prevents dimension mismatch errors
7. **The Programming Perspective** — NumPy/TensorFlow notation, broadcasting hints
8. **Common Pitfalls** — Shape mismatches, confusing element-wise vs matrix multiply

**Tone**: Conversational but precise. Use code analogies (matrices as 2D arrays, multiplication as nested loops). Include TypeScript-style pseudocode where helpful.

**Length**: Comprehensive — approximately 1800-2200 words with clear section headings and worked examples.
```

### A2 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A2
**Title**: Matrix Multiplication Visualizer
**Description**: Animate row-by-column multiplication step-by-step. Show matrices transforming space (rotation, scaling, shearing).

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User has completed A1 (Vector Operations)
- Understands vectors as arrows

**Learning Objectives the visualization must support**:
1. See how each output element is computed (row · column)
2. Understand dimension requirements for multiplication
3. Visualize matrices transforming 2D space
4. See why multiplication order changes the result

**Required Interactive Features**:

**Mode 1: Arithmetic View**
1. **Matrix Input**: Editable matrix cells (2×2, 2×3, 3×3 presets)
2. **Step-by-Step Animation**:
   - Highlight current row of matrix A
   - Highlight current column of matrix B
   - Animate dot product calculation
   - Fill in result cell with computed value
3. **Speed Control**: Slow/medium/fast animation
4. **Dimension Indicator**: Show (m×n) × (n×p) = (m×p)

**Mode 2: Transformation View**
1. **Grid of Points**: Unit square or shape made of points
2. **Matrix Selector**: Preset transformations (rotation, scale, shear, reflection)
3. **Custom Matrix**: Edit transformation matrix values
4. **Apply Animation**: Watch points smoothly transform
5. **Composition Demo**: Apply matrix A, then matrix B, show it equals AB applied once
6. **Order Toggle**: Compare AB vs BA transformations

**Visual Design Requirements**:
- Matrix cells clearly visible with grid lines
- Color coding: Row highlight, Column highlight, Result highlight
- Transformation view: before (ghost) and after positions
- Animated trails showing point movement
- Clear labels for matrix names (A, B, C = A×B)

**Code Architecture Requirements**:
- Separate modules for arithmetic view and transformation view
- Matrix class with multiplication method
- Animation timeline system for step control
- State management for current step in calculation
- TypeScript interfaces for Matrix types

**Deliverables**:
1. Complete TypeScript implementation
2. HTML/CSS for UI controls
3. Clear code comments explaining the math at each step
4. README with usage instructions

Provide complete, runnable code.
```

---

## A3: Matrix Transformations Gallery

### A3 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Matrix Transformations — Composition and Order Effects

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will explore composing transformation matrices interactively and see why multiplication order matters.

**Prerequisites the learner should already understand**:
- Vectors (A1) and Matrix Multiplication (A2)
- How a single matrix can transform space

**Learning Objectives** — After reading this explanation, the learner should:
1. Recognize the standard 2D/3D transformation matrices by sight
2. Understand how to compose multiple transformations into one matrix
3. Predict the effect of multiplication order on composed transformations
4. Understand homogeneous coordinates for translations
5. Connect transformation composition to neural network layer stacking

**Required Sections**:
1. **The Transformation Zoo** — Reference for each type:
   - Identity matrix
   - Scaling (uniform and non-uniform)
   - Rotation (2D and 3D around each axis)
   - Shearing
   - Reflection
   - Translation (requires homogeneous coordinates)
2. **Composition: Combining Transformations** — Multiplying matrices chains their effects
3. **Order Matters: A Visual Proof** — "Rotate then translate" vs "translate then rotate" with clear diagrams
4. **Reading Order Convention** — Right-to-left application (why AB means "apply B first, then A")
5. **Homogeneous Coordinates** — Why we need 3×3 for 2D, 4×4 for 3D to include translation
6. **Why This Matters for ML/AI**:
   - Neural networks stack transformations (layers)
   - Each layer transforms feature space
   - Data augmentation uses these transformations
   - Understanding composition helps debug shape issues
7. **Building Complex Transforms** — Example: rotate around arbitrary point

**Tone**: Practical and visual. Emphasize intuition over formulas, but include matrices for reference.

**Length**: Approximately 1500-1800 words with transformation matrices shown clearly.
```

### A3 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A3
**Title**: Matrix Transformations Gallery
**Description**: Compose transformation matrices interactively. Demonstrate multiplication order effects.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User has completed A1 and A2
- Understands basic matrix transformations

**Learning Objectives the visualization must support**:
1. See each transformation type in action
2. Compose multiple transformations
3. Observe order-dependent results
4. Build intuition for transformation design

**Required Interactive Features**:

**Transformation Palette**:
1. **Preset Buttons**: Scale, Rotate, Shear, Reflect, Translate
2. **Parameter Sliders** for each:
   - Scale: x-factor, y-factor (0.1 to 3)
   - Rotate: angle (0° to 360°)
   - Shear: x-shear, y-shear (-2 to 2)
   - Translate: x-offset, y-offset (-5 to 5)

**Composition Stack**:
1. **Add Transformation**: Button adds selected transform to stack
2. **Reorder**: Drag to reorder transformations in stack
3. **Remove**: Delete transformations from stack
4. **Stack Display**: Show each matrix in the stack with its parameters
5. **Combined Matrix**: Display the composed result matrix

**Visualization Canvas**:
1. **Shape Selector**: Unit square, house shape, letter F, custom polygon
2. **Original Ghost**: Faded outline of original shape
3. **Transformed Shape**: Solid colored result
4. **Step-Through Mode**: Apply transformations one at a time with animation
5. **Comparison Mode**: Side-by-side of two different orderings

**Order Demonstration**:
1. **Quick Compare Button**: Automatically shows AB vs BA for current stack
2. **Highlight Differences**: Emphasize where the results differ

**Visual Design Requirements**:
- Clear grid with origin marked
- Shape fills with distinct colors
- Transformation stack as vertical list with matrix previews
- Smooth animated transitions between steps
- Color-coded transformation types

**Code Architecture Requirements**:
- Transformation factory functions
- Matrix composition utility
- Undo/redo stack
- Animation queue system
- Clean separation of UI and math logic

**Deliverables**:
Complete TypeScript implementation with all features, modular architecture, and comprehensive comments.
```

---

## A4: Tensor Visualiser

### A4 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Tensors — From Scalars to N-Dimensional Arrays

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see tensors of increasing dimensionality and operations like reshaping, broadcasting, and slicing.

**Prerequisites the learner should already understand**:
- Vectors (A1) and Matrices (A2)
- Arrays in programming
- Basic neural network concepts (helpful but not required)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the tensor hierarchy: scalar → vector → matrix → 3D tensor → N-D tensor
2. Know what tensor "shape" and "rank" mean
3. Understand reshaping and why it's useful
4. Grasp broadcasting rules intuitively
5. Know how to slice and index tensors
6. Connect tensor operations to neural network data flow

**Required Sections**:
1. **What is a Tensor?** — Generalization of vectors and matrices to any number of dimensions
2. **The Tensor Hierarchy**:
   - Rank 0: Scalar (single number) — a loss value
   - Rank 1: Vector (1D array) — a bias vector
   - Rank 2: Matrix (2D array) — a weight matrix, grayscale image
   - Rank 3: 3D tensor — RGB image (height × width × channels), batch of vectors
   - Rank 4+: Batch of images, video, etc.
3. **Shape, Rank, and Size**:
   - Shape: tuple of dimension sizes
   - Rank: number of dimensions
   - Size: total number of elements
4. **Reshaping** — Same data, different shape
   - Flattening (image to vector for dense layer)
   - Expanding dimensions (for broadcasting)
   - Common reshapes in neural networks
5. **Broadcasting** — How operations work on mismatched shapes
   - Rules explained simply
   - Visual examples
   - Common broadcasting patterns in ML
6. **Slicing and Indexing** — Extracting sub-tensors
   - Single element access
   - Slice notation
   - Advanced indexing
7. **Why This Matters for ML/AI**:
   - All neural network data is tensors
   - Shape errors are the most common bugs
   - Understanding broadcasting prevents confusion
   - Reshaping connects different layer types

**Include**: TensorFlow.js and NumPy code snippets showing each operation.

**Length**: Approximately 2000-2500 words with clear diagrams described and code examples.
```

### A4 — Three.js Visualization Prompt

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

---

## A5: Eigenvalues & Eigenvectors

### A5 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Eigenvalues and Eigenvectors

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see eigenvectors as special vectors that only scale (don't rotate) under matrix transformation.

**Prerequisites the learner should already understand**:
- Vectors and vector operations (A1)
- Matrix transformations (A2, A3)
- What scaling a vector means

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand eigenvectors as "direction-preserving" vectors under transformation
2. Know that eigenvalues tell us the scaling factor
3. Visualize what eigenvectors look like for various matrices
4. Understand the connection to PCA (dimensionality reduction)
5. Grasp why eigen-decomposition reveals matrix structure

**Required Sections**:
1. **The Key Intuition** — Most vectors get rotated and scaled by a matrix. Eigenvectors only get scaled.
2. **Definition Made Visual**:
   - Av = λv explained in plain language
   - "A transforms v to a scaled version of itself"
3. **Finding Eigenvectors** — High-level process (not full computation):
   - det(A - λI) = 0 to find eigenvalues
   - Solve (A - λI)v = 0 for eigenvectors
4. **Visual Examples**:
   - 2×2 scaling matrix (easy case: axis vectors are eigenvectors)
   - 2×2 rotation matrix (no real eigenvectors — everything rotates)
   - Shear matrix (one eigenvector along shear axis)
   - Symmetric matrix (orthogonal eigenvectors)
5. **Eigenvalue Meaning**:
   - λ > 1: stretching
   - 0 < λ < 1: compression
   - λ < 0: flip direction
   - λ = 0: collapse to lower dimension
6. **Why This Matters for ML/AI**:
   - **PCA**: Eigenvectors of covariance matrix are principal components
   - **Stability Analysis**: Gradient descent convergence
   - **Graph Neural Networks**: Spectral methods use Laplacian eigenvectors
   - **SVD**: Closely related (singular values)
7. **Connection to PCA** — Eigenvectors point in directions of maximum variance

**Tone**: Focus heavily on visual intuition. Math notation is secondary to understanding.

**Length**: Approximately 1600-2000 words with emphasis on examples and ML applications.
```

### A5 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A5
**Title**: Eigenvalues & Eigenvectors Visualizer
**Description**: Vectors that only scale under transformation. Link to PCA for dimensionality reduction.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands matrix transformations

**Learning Objectives the visualization must support**:
1. See that most vectors rotate AND scale under transformation
2. See eigenvectors only scale (stay on same line)
3. Understand eigenvalue as the scaling factor
4. Connect to PCA (bonus view)

**Required Interactive Features**:

**Main Exploration View**:
1. **Matrix Input**: Editable 2×2 matrix
2. **Matrix Presets**:
   - Scaling (diagonal) — easy eigenvectors
   - Rotation — no real eigenvectors
   - Shear — one eigenvector
   - Symmetric — orthogonal eigenvectors
3. **Vector Field Display**: Grid of vectors before/after transformation
4. **Highlight Eigenvectors**: Special color for eigenvector directions
5. **Interactive Vector**: Drag a vector, see its transformation
   - Changes color when aligned with eigenvector direction
   - Shows "only scaling!" indicator when on eigenvector

**Eigenspace View**:
1. **Eigenvector Arrows**: Display computed eigenvectors
2. **Eigenvalue Labels**: Show λ₁, λ₂ values
3. **Animation**: Apply matrix repeatedly, show eigenvectors are stable directions
4. **Scaling Indicator**: Visual showing stretch/compress amount

**PCA Connection View** (bonus):
1. **Data Cloud**: 2D scatter plot of data points
2. **Covariance Ellipse**: Show data spread
3. **Principal Components**: Eigenvectors of covariance as arrows
4. **Projection Demo**: Project data onto PC1, show variance preserved

**Visual Design Requirements**:
- Vector field with consistent base positions
- Clear before/after states (ghost vs solid)
- Eigenvector directions as dashed infinite lines through origin
- Eigenvalue magnitude shown by arrow thickness or glow
- Color coding: λ > 0 (one color), λ < 0 (another color)

**Code Architecture Requirements**:
- Numeric eigenvector computation (power iteration or analytic for 2×2)
- Vector field renderer
- Smooth transformation animations
- Clear separation between math computation and rendering

**Deliverables**:
Complete TypeScript implementation with eigenvector highlighting, interactive exploration, and optional PCA view.
```

---

## A6: Basis Vectors & Change of Basis

### A6 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Basis Vectors and Change of Basis

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see the same point described in different coordinate systems and understand how basis vectors define a coordinate system.

**Prerequisites the learner should already understand**:
- Vectors and vector operations (A1)
- Matrix multiplication as transformation (A2)
- Basic coordinate systems

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand that basis vectors define a coordinate system
2. Know that any vector can be written as a linear combination of basis vectors
3. Understand how the same point has different coordinates in different bases
4. Know how to convert between coordinate systems using matrices
5. Connect basis to neural network embeddings and feature spaces

**Required Sections**:
1. **What are Basis Vectors?** — The "measuring sticks" of a coordinate system
2. **Standard Basis** — The i, j, k vectors we take for granted
3. **Linear Combinations** — Every vector = sum of scaled basis vectors
4. **Non-Standard Bases** — Using different measuring sticks
5. **Same Point, Different Coordinates** — The key insight
   - A position doesn't change
   - Its numeric description depends on the basis
6. **Change of Basis Matrix** — Converting coordinates between systems
7. **Why This Matters for ML/AI**:
   - **Embeddings**: Words/images represented in learned basis
   - **Feature Spaces**: Different layers = different coordinate systems
   - **PCA**: Finding a better basis for your data
   - **Attention**: Query/Key/Value are different projections (bases)
   - **Transfer Learning**: Aligning embedding spaces
8. **Visual Intuition** — Grid lines changing when basis changes

**Tone**: Emphasize the intuition that coordinates are just descriptions relative to a chosen reference. Use real-world analogies (different maps of the same territory).

**Length**: Approximately 1400-1800 words with clear examples.
```

### A6 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: A6
**Title**: Basis Vectors & Change of Basis
**Description**: Same point in different coordinate systems. Foundation for embedding spaces.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands vectors and matrix operations

**Learning Objectives the visualization must support**:
1. See basis vectors as coordinate system defining arrows
2. Watch grid transform when basis changes
3. See same point with different coordinate values
4. Understand change of basis as matrix operation

**Required Interactive Features**:

**Dual View Mode**:
1. **Side-by-Side Canvases**:
   - Left: Standard basis (i = [1,0], j = [0,1])
   - Right: Custom basis
2. **Linked Point**: Same geometric point shown in both, with different coordinates displayed
3. **Draggable Point**: Move point, watch coordinates update in both views

**Basis Editor**:
1. **Draggable Basis Vectors**: Click and drag to modify custom basis
2. **Numeric Input**: Direct entry of basis vector components
3. **Preset Bases**:
   - Standard basis
   - Rotated basis (45°)
   - Scaled basis
   - Skewed basis
4. **Grid Visualization**: Grid lines aligned with basis vectors

**Transformation View**:
1. **Change of Basis Matrix**: Display the matrix that converts coordinates
2. **Animate Conversion**: Show coordinates transforming through matrix multiplication
3. **Inverse Matrix**: Show conversion back to standard basis

**Embedding Analogy Section** (bonus):
1. **Word Example**: Show how "king" might have coordinates in embedding space
2. **Different Bases = Different Features**: Visualize re-projecting to different meaningful axes

**Visual Design Requirements**:
- Clear, labeled basis vectors (e.g., b₁, b₂ or custom labels)
- Grid that morphs with basis
- Point with coordinate readout in both systems
- Smooth animation when basis changes
- Different colors for each coordinate system's grid

**Code Architecture Requirements**:
- Basis class with transformation methods
- Synchronized dual canvas rendering
- Coordinate conversion utilities
- Animation interpolation for smooth basis transitions

**Deliverables**:
Complete TypeScript implementation with dual-view display, draggable elements, and clear coordinate readouts.
```

---

## Summary

| ID | Title | Education Prompt | Visualization Prompt |
|----|-------|------------------|---------------------|
| A1 | Vector Operations | ✅ | ✅ |
| A2 | Matrix Multiplication | ✅ | ✅ |
| A3 | Matrix Transformations Gallery | ✅ | ✅ |
| A4 | Tensor Visualiser | ✅ | ✅ |
| A5 | Eigenvalues & Eigenvectors | ✅ | ✅ |
| A6 | Basis Vectors & Change of Basis | ✅ | ✅ |
