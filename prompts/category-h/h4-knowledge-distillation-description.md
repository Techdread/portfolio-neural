# H4: Knowledge Distillation — Educational Explanation Prompt

## Topic
Knowledge Distillation — Teaching a Small Model from a Large One

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see the teacher → student knowledge transfer process visualized.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Knowledge Distillation — Teaching a Small Model from a Large One

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see the teacher → student knowledge transfer process visualized.

**Prerequisites the learner should already understand**:
- Neural network training (C1, C2)
- Softmax and probabilities (C6)
- What model size/complexity means

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand the motivation (deploy small, train large)
2. Know the teacher-student framework
3. Understand soft labels vs hard labels
4. See how temperature affects softmax
5. Know the distillation loss

**Required Sections**:
1. **The Problem** — Large models are accurate but expensive to deploy
2. **The Idea** — Train small model to mimic large model's behavior
3. **Teacher and Student**:
   - Teacher: large, accurate, pre-trained model
   - Student: small, fast, to be trained
   - Goal: student learns to predict like teacher
4. **Why Not Just Train Small Model on Data?**:
   - Hard labels (0/1) lose information
   - Teacher's soft outputs capture more: "It's 70% cat, 25% dog, 5% tiger"
   - Soft labels provide richer supervision
5. **Temperature in Softmax**:
   - Higher temperature → softer distribution
   - Reveals "dark knowledge" in small probabilities
   - Teacher and student use same temperature
6. **Distillation Loss**:
   - Match student's soft outputs to teacher's soft outputs
   - Often combined with standard hard label loss
   - Loss = α × soft_loss + (1-α) × hard_loss
7. **What Gets Transferred**:
   - Relative probabilities between classes
   - Inter-class relationships
   - Teacher's mistakes also teach (what NOT to predict)
8. **Why This Matters for ML/AI**:
   - Deploy BERT-like quality on mobile
   - Edge inference with limited compute
   - Foundation of many efficient model techniques

**Tone**: Emphasize the "teaching" metaphor. Make knowledge transfer feel intuitive.

**Length**: Approximately 1600-2000 words with clear pipeline explanation.
```
