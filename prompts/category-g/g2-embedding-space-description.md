# G2: Embedding Space Explorer — Educational Explanation Prompt

## Topic
Embedding Spaces — Representing Words and Images as Vectors

## Context
This is part of an interactive Three.js visualization portfolio. The learner will explore word2vec/image embeddings in 3D using t-SNE/UMAP, searching and discovering relationships.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Embedding Spaces — Representing Words and Images as Vectors

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will explore word2vec/image embeddings in 3D using t-SNE/UMAP, searching and discovering relationships.

**Prerequisites the learner should already understand**:
- Vectors as points in space (A1)
- Dot products as similarity (A1)
- Neural network basics (C1)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand embeddings as learned vector representations
2. Know that similar items have nearby vectors
3. Understand dimensionality reduction (t-SNE, UMAP) for visualization
4. See famous examples (king - man + woman = queen)
5. Know applications of embeddings

**Required Sections**:
1. **What is an Embedding?** — Converting discrete items (words, images) to continuous vectors
2. **Why Embeddings?**:
   - Neural networks need numbers
   - One-hot encoding is sparse and meaningless
   - Embeddings capture semantic meaning
3. **Word Embeddings (word2vec)**:
   - Words → 100-300 dimensional vectors
   - Similar words = nearby vectors
   - Famous: king - man + woman ≈ queen
   - Trained on word co-occurrence
4. **Image Embeddings**:
   - Images → feature vectors
   - Similar images = nearby vectors
   - From CNN layers or dedicated embedding models
5. **The High-Dimensional Challenge**:
   - Embeddings have 100s of dimensions
   - Can't visualize directly
   - Need dimensionality reduction
6. **t-SNE and UMAP**:
   - Reduce to 2D or 3D for visualization
   - Preserve local neighborhood structure
   - Similar items stay close
   - Different items pushed apart
7. **Exploring Embedding Space**:
   - Clusters = semantic groups
   - Directions = semantic relationships
   - Arithmetic = analogy completion
8. **Why This Matters for ML/AI**:
   - Embeddings everywhere: NLP, vision, recommender systems
   - Foundation for transformers and LLMs
   - Understanding embeddings = understanding modern AI

**Tone**: Focus on the "meaning as position" insight. Make semantic space feel tangible.

**Length**: Approximately 1800-2200 words with concrete examples and analogies.
```
