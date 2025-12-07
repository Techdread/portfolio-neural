# E2: Transformer Attention Visualiser — Educational Explanation Prompt

## Topic
Transformer Attention Mechanism

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see attention heads as connection strengths between tokens.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Transformer Attention Mechanism

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see attention heads as connection strengths between tokens.

**Prerequisites the learner should already understand**:
- Matrix multiplication (A2)
- Softmax (C6)
- Neural network basics

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the motivation for attention (handling long sequences)
2. Know the Query, Key, Value framework
3. See attention weights as "how much to focus on each token"
4. Understand multi-head attention
5. Know why transformers dominate NLP and beyond

**Required Sections**:
1. **The Problem with Sequences** — RNNs struggle with long-range dependencies
2. **Attention Intuition** — "Look at relevant parts of the input"
3. **Query, Key, Value**:
   - Query: "What am I looking for?"
   - Key: "What do I contain?"
   - Value: "What do I offer?"
   - Analogy: searching a database
4. **The Attention Formula**:
   - Attention(Q, K, V) = softmax(QK^T / √d) × V
   - Similarity = dot product
   - Scale by √d for stable gradients
   - Softmax for weights summing to 1
5. **Self-Attention** — Tokens attending to other tokens in same sequence
6. **Multi-Head Attention**:
   - Multiple attention "perspectives"
   - Each head learns different relationships
   - Heads combined at the end
7. **Position Encoding** — Adding position information (attention is order-agnostic)
8. **Why This Matters for ML/AI**:
   - Transformers power GPT, BERT, and most modern NLP
   - Attention now used in vision (ViT), audio, and more
   - Understanding attention = understanding modern AI

**Tone**: Demystify attention. Use the "looking" and "focusing" metaphors. Make QKV intuitive.

**Length**: Approximately 2000-2500 words with clear QKV explanation and intuition.
```
