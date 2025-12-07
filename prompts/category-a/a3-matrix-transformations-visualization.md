# A3: Matrix Transformations Gallery — Three.js Visualization Prompt

## Visualization ID
A3

## Title
Matrix Transformations Gallery

## Description
Compose transformation matrices interactively. Demonstrate multiplication order effects.

---

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
