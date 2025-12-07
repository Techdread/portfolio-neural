# G2: Embedding Space Explorer — Three.js Visualization Prompt

## Visualization ID
G2

## Title
Embedding Space Explorer

## Description
word2vec/image embeddings in 3D with t-SNE/UMAP. Search and explore relationships.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: G2
**Title**: Embedding Space Explorer
**Description**: word2vec/image embeddings in 3D with t-SNE/UMAP. Search and explore relationships.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands vectors as positions

**Learning Objectives the visualization must support**:
1. See items as points in 3D space
2. Discover clusters of similar items
3. Explore relationships via search
4. Try vector arithmetic (analogies)

**Required Interactive Features**:

**3D Space View**:
1. **Point Cloud**: Hundreds/thousands of embedded items
2. **Camera Controls**: Orbit, pan, zoom
3. **Point Labels**: Show label on hover
4. **Point Colors**: Color by category/cluster
5. **Cluster Highlighting**: Visual cluster boundaries

**Dataset Options**:
1. **Word Embeddings**: Common English words (500-2000)
2. **Country Embeddings**: Countries with geographic/economic clusters
3. **MNIST Digits**: Handwritten digit images
4. **Custom Upload**: Load own embeddings (JSON format)

**Search and Select**:
1. **Search Box**: Type to find specific items
2. **Search Results**: Dropdown of matches
3. **Jump to Item**: Center view on searched item
4. **Multi-Select**: Select multiple items
5. **Selected Panel**: Show selected items list

**Nearest Neighbors**:
1. **Select Point**: Click to select
2. **Show Neighbors**: Highlight N nearest neighbors
3. **Neighbor Count Slider**: How many neighbors to show
4. **Connection Lines**: Draw lines to neighbors
5. **Similarity Scores**: Show distances/similarities

**Vector Arithmetic** (analogy mode):
1. **Formula Builder**: "A - B + C = ?"
2. **Select Items**: Click to fill A, B, C slots
3. **Compute Result**: Find nearest point to result vector
4. **Famous Examples**: Preset king-man+woman=queen
5. **Visualize Operation**: Show vectors being added/subtracted

**Dimensionality Reduction Display**:
1. **Algorithm Toggle**: t-SNE vs UMAP
2. **Perplexity/Neighbors Slider**: Algorithm parameters
3. **Re-compute Button**: Recalculate projection
4. **Original Dimension Info**: Show true embedding dimension

**Cluster Analysis**:
1. **Auto-Cluster**: K-means or similar
2. **Cluster Colors**: Each cluster distinct color
3. **Cluster Labels**: Inferred or manual labels
4. **Inter-Cluster Distance**: Show relationships between clusters

**Visual Design Requirements**:
- Dense but navigable point cloud
- Readable labels on hover
- Smooth camera transitions
- Clear selection highlighting
- Intuitive analogy interface

**Code Architecture Requirements**:
- Embedding data loading/parsing
- Efficient point cloud rendering (BufferGeometry)
- Spatial index for nearest neighbor queries
- Vector arithmetic utilities
- Camera and interaction management

**Deliverables**:
Complete TypeScript implementation with 3D exploration, search, nearest neighbors, and vector arithmetic interface.
```
