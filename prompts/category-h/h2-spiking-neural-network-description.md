# H2: Spiking Neural Network — Educational Explanation Prompt

## Topic
Spiking Neural Networks — Biological Inspiration and Neuromorphic Computing

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see temporal spike propagation dynamics, introducing them to neuromorphic computing concepts.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Spiking Neural Networks — Biological Inspiration and Neuromorphic Computing

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see temporal spike propagation dynamics, introducing them to neuromorphic computing concepts.

**Prerequisites the learner should already understand**:
- Basic neural network concepts (C1)
- What biological neurons do (very basic)
- Time-based vs static processing

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand how SNNs differ from traditional ANNs
2. Know the leaky integrate-and-fire neuron model
3. Understand spikes as discrete events in time
4. See the potential advantages (efficiency, temporal data)
5. Know about neuromorphic hardware

**Required Sections**:
1. **Traditional ANNs vs SNNs**:
   - ANNs: continuous activations, one forward pass
   - SNNs: discrete spikes over time, temporal dynamics
2. **Biological Inspiration**:
   - Real neurons communicate via action potentials (spikes)
   - Spike timing matters
   - Energy efficient (neurons fire sparsely)
3. **Leaky Integrate-and-Fire (LIF) Neuron**:
   - Membrane potential accumulates input
   - "Leaks" over time (decays)
   - Fires spike when threshold reached
   - Resets after firing (refractory period)
4. **Spike Encoding**:
   - Rate coding: frequency of spikes = intensity
   - Temporal coding: timing of spikes carries information
   - Population coding: patterns across neurons
5. **Spike Propagation**:
   - Input spikes affect downstream neurons
   - Temporal patterns propagate through network
   - Timing-dependent effects
6. **Training SNNs**:
   - STDP: Spike-Timing Dependent Plasticity
   - Surrogate gradients for backprop
   - Still an active research area
7. **Neuromorphic Hardware**:
   - Intel Loihi, IBM TrueNorth
   - Extremely energy efficient
   - Good for edge devices, always-on sensing
8. **Why This Matters for ML/AI**:
   - Alternative paradigm to current deep learning
   - Potential for massive efficiency gains
   - Better for temporal/event-based data
   - Growing research interest

**Tone**: Emphasize the biological connection and future potential. Make spikes feel dynamic and alive.

**Length**: Approximately 1700-2100 words introducing this alternative paradigm clearly.
```
