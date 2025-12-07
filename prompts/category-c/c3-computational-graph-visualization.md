# C3: Computational Graph — Three.js Visualization Prompt

## Visualization ID
C3

## Title
Computational Graph Visualizer

## Description
Expression trees for functions. Autodiff traversing forwards and backwards.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C3
**Title**: Computational Graph Visualizer
**Description**: Expression trees for functions. Autodiff traversing forwards and backwards.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands forward/backward passes
- User understands chain rule

**Learning Objectives the visualization must support**:
1. See expressions as visual graphs
2. Watch values flow forward through operations
3. Watch gradients flow backward through operations
4. Understand local gradient rules for each operation type

**Required Interactive Features**:

**Graph Construction**:
1. **Preset Expressions**:
   - Simple: x² + y
   - Medium: x×y + sin(x)
   - Complex: (x + y)² × z
2. **Custom Expression Input**: Text box to enter formula
3. **Visual Graph Building**: Drag-and-drop node creation (advanced)

**Graph Display**:
1. **Tree Layout**: Operations as nodes, data flow as edges
2. **Node Types** (distinct shapes/colors):
   - Input nodes (circles)
   - Operation nodes (rectangles with symbol: +, ×, ^, sin)
   - Output node (diamond)
3. **Edge Labels**: Show data flowing on edges
4. **Expandable Nodes**: Click to see operation details

**Forward Evaluation**:
1. **Input Value Sliders**: Set values for input variables
2. **Animate Forward Button**: Watch evaluation flow leaves → root
3. **Step-by-Step Mode**: One operation at a time
4. **Value Labels**: Show computed value at each node after evaluation

**Backward Differentiation**:
1. **Start Backward Button**: Begin gradient propagation
2. **Gradient Flow Animation**: Watch gradients flow root → leaves
3. **Local Rule Display**: Show the backward rule being applied at each node
4. **Gradient Values**: Show ∂output/∂node at each node
5. **Final Gradients**: Display ∂output/∂x, ∂output/∂y, etc.

**Rule Reference Panel**:
1. **Operation List**: Show backward rule for each operation type
2. **Current Operation**: Highlight rule being used

**Visual Design Requirements**:
- Clear hierarchical graph layout (root at top or left)
- Distinct visual treatment for forward vs backward mode
- Animated flow along edges
- Node highlighting during computation
- Clean, readable formulas/values

**Code Architecture Requirements**:
- Expression parser (text → graph)
- Graph node classes with forward() and backward() methods
- Graph traversal algorithms
- Layout algorithm for graph visualization
- Animation sequencing system

**Deliverables**:
Complete TypeScript implementation with expression parsing, graph visualization, and animated forward/backward traversal.
```
