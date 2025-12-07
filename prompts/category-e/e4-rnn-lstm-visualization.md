# E4: RNN/LSTM Unrolled — Three.js Visualization Prompt

## Visualization ID
E4

## Title
RNN/LSTM Unrolled

## Description
Show temporal unrolling, hidden state persistence, gate operations.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: E4
**Title**: RNN/LSTM Unrolled
**Description**: Show temporal unrolling, hidden state persistence, gate operations.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic neural networks

**Learning Objectives the visualization must support**:
1. See RNN as same cell repeated over time
2. Watch hidden state flow between timesteps
3. Understand LSTM gates visually
4. See information flow through cell state

**Required Interactive Features**:

**Basic RNN View**:
1. **Rolled View**: Single RNN cell with loop arrow (recurrence)
2. **Unroll Button**: Animate unrolling into timeline
3. **Unrolled View**: Copies of cell at each timestep
4. **Hidden State Arrows**: Show h passing between steps

**Sequence Input**:
1. **Input Sequence**: Editable text or numbers
2. **Timestep Markers**: Label each input position
3. **Current Timestep Indicator**: Highlight active step
4. **Step Forward/Back**: Move through sequence

**Hidden State Visualization**:
1. **State Vector Display**: Show hidden state values
2. **State Evolution**: Watch state change through time
3. **Color Coding**: Activation intensity as color
4. **State History**: Trail showing how state evolved

**LSTM Cell View**:
1. **Detailed Cell Diagram**: Show all LSTM components
2. **Gates Labeled**: Forget, Input, Output gates
3. **Cell State Highway**: The C_t line running through
4. **Gate Values**: Show sigmoid outputs (0-1)

**Gate Animation**:
1. **Input Arrives**: Show x_t and h_{t-1} entering
2. **Compute Gates**: Animate gate value computation
3. **Forget Step**: Show cell state being masked
4. **Input Step**: Show new information being added
5. **Output Step**: Show hidden state being computed
6. **Step-by-Step Mode**: One operation at a time

**Gate Interactive Mode**:
1. **Manual Gate Sliders**: Adjust forget, input, output gates
2. **See Effect**: Watch how gates affect information flow
3. **Extreme Values**: Set gates to 0 or 1 to see full block/pass

**Comparison View**:
1. **RNN vs LSTM Toggle**: Switch between architectures
2. **Gradient Flow Overlay**: Show how gradients flow differently
3. **Long Sequence Demo**: See vanishing gradient in RNN

**Visual Design Requirements**:
- Clear cell boundaries
- Smooth animations for unrolling
- Gate values as fill levels or bar heights
- Information flow as animated pulses
- Clean timeline layout for unrolled view

**Code Architecture Requirements**:
- RNN/LSTM cell classes
- State management for timesteps
- Gate computation functions
- Animation sequencing
- Interactive gate control

**Deliverables**:
Complete TypeScript implementation with RNN unrolling, LSTM gate visualization, step-by-step animation, and interactive exploration.
```
