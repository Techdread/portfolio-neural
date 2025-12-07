# E4: RNN/LSTM Unrolled — Educational Explanation Prompt

## Topic
Recurrent Neural Networks and LSTM — Processing Sequences

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see temporal unrolling, hidden state persistence, and gate operations in LSTMs.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Recurrent Neural Networks and LSTM — Processing Sequences

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see temporal unrolling, hidden state persistence, and gate operations in LSTMs.

**Prerequisites the learner should already understand**:
- Neural network basics (C1)
- What sequences are (text, time series)
- Backpropagation basics (C2)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand RNNs as networks with memory
2. Know what "unrolling" means
3. Understand hidden state as carried information
4. Know the vanishing gradient problem in RNNs
5. Understand LSTM gates and cell state

**Required Sections**:
1. **The Sequence Problem** — Previous inputs affect current output
2. **RNN Core Idea**:
   - Process one timestep at a time
   - Hidden state passes information forward
   - Same weights used at each timestep
3. **Unrolling Through Time**:
   - Visualize RNN as copies at each timestep
   - Connections between timesteps via hidden state
   - Backprop through time (BPTT)
4. **Hidden State as Memory**:
   - Accumulates information from past
   - Compressed representation of history
   - Gets updated at each step
5. **The Vanishing Gradient Problem**:
   - Gradients shrink through many timesteps
   - Hard to learn long-range dependencies
   - Why standard RNNs struggle with long sequences
6. **LSTM Solution**:
   - Cell state: highway for information
   - Gates control information flow
   - Forget gate: what to discard
   - Input gate: what new information to add
   - Output gate: what to output
7. **Gate Mechanics**:
   - Sigmoid for gate values (0-1)
   - Element-wise multiplication to allow/block
   - Learn when to remember and forget
8. **Why This Matters for ML/AI**:
   - RNNs/LSTMs for sequence modeling
   - Replaced by transformers in many tasks, but still used
   - Understanding helps with any sequential data

**Tone**: Focus on the "memory" metaphor. Make gates intuitive with "keep/forget" language.

**Length**: Approximately 2000-2500 words covering both RNN and LSTM thoroughly.
```
