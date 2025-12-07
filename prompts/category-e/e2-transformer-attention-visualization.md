# E2: Transformer Attention Visualiser — Three.js Visualization Prompt

## Visualization ID
E2

## Title
Transformer Attention Visualiser

## Description
Attention heads as connection strengths between tokens.

---

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
