# H2: Spiking Neural Network — Three.js Visualization Prompt

## Visualization ID
H2

## Title
Spiking Neural Network

## Description
Temporal spike propagation dynamics. Neuromorphic computing intro.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: H2
**Title**: Spiking Neural Network
**Description**: Temporal spike propagation dynamics. Neuromorphic computing intro.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target with many neurons

**Prerequisites for this visualization**:
- User understands basic neural network concepts

**Learning Objectives the visualization must support**:
1. See neurons as temporal processing units
2. Watch membrane potential rise, spike, and reset
3. See spikes propagate through layers
4. Understand the temporal dimension

**Required Interactive Features**:

**Network Display**:
1. **3D Neuron Layout**: Neurons as spheres in layers
2. **Connection Lines**: Synapses between neurons
3. **Spike Animation**: Visual flash/pulse when neuron fires
4. **Spike Propagation**: Animated signals along connections

**Single Neuron View**:
1. **LIF Neuron Diagram**: Detailed view of one neuron
2. **Membrane Potential Plot**: Real-time voltage trace
3. **Threshold Line**: Horizontal line showing firing threshold
4. **Spike Markers**: Vertical lines when spikes occur
5. **Decay Visualization**: Show potential leaking down

**Time Controls**:
1. **Time Slider**: Scrub through simulation
2. **Play/Pause**: Run simulation
3. **Speed Control**: Slow motion to fast forward
4. **Step Mode**: Advance by single timestep
5. **Time Display**: Current simulation time

**Input Control**:
1. **Input Spike Pattern**: Define input spike times
2. **Preset Patterns**:
   - Regular train (constant frequency)
   - Burst (rapid spikes then pause)
   - Random Poisson
3. **Input Rate Slider**: Average firing rate
4. **Manual Trigger**: Click to inject spike

**Neuron Parameters**:
1. **Threshold Slider**: Firing threshold voltage
2. **Leak Rate Slider**: How fast potential decays
3. **Refractory Period**: Time after spike before can fire again
4. **Synaptic Weight Slider**: Connection strength

**Network Simulation**:
1. **Layer Configuration**: Input → Hidden → Output
2. **Watch Propagation**: See spikes travel through layers
3. **Population Activity**: Raster plot of all neurons
4. **Firing Rate Display**: Spikes per second for each neuron

**Encoding Demonstration**:
1. **Rate Coding Mode**: Input intensity → spike frequency
2. **Image to Spikes**: Convert image pixels to spike rates
3. **Output Decoding**: How to read output spikes

**Visual Design Requirements**:
- Dynamic, pulsing neuron animations
- Spike trails along connections
- Real-time membrane potential plots
- Color coding for neuron state (resting, rising, firing, refractory)
- Smooth time-based animations

**Code Architecture Requirements**:
- LIF neuron class with update method
- Network simulation loop
- Spike event management
- Time-series data storage for plots
- Efficient many-neuron rendering

**Deliverables**:
Complete TypeScript implementation with LIF neurons, spike propagation visualization, membrane potential plots, and temporal controls.
```
