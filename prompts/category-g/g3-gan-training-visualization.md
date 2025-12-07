# G3: GAN Training Dance — Three.js Visualization Prompt

## Visualization ID
G3

## Title
GAN Training Dance

## Description
Generator vs discriminator loss tug-of-war, generated outputs evolving.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: G3
**Title**: GAN Training Dance
**Description**: Generator vs discriminator loss tug-of-war, generated outputs evolving.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable), TensorFlow.js (optional for real training)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands neural networks and loss functions

**Learning Objectives the visualization must support**:
1. See the two-player game visually
2. Watch loss curves evolve with seesaw pattern
3. See generated outputs improve over time
4. Understand training dynamics

**Required Interactive Features**:

**Architecture View**:
1. **Two Network Boxes**: Generator and Discriminator
2. **Data Flow**:
   - Noise → Generator → Fake Image
   - Real Image → Discriminator → Real/Fake score
   - Fake Image → Discriminator → Real/Fake score
3. **Connection Arrows**: Showing data paths
4. **Current Phase Indicator**: "Training Generator" or "Training Discriminator"

**Loss Curves**:
1. **Dual Plot**: G loss and D loss over time
2. **Real-Time Update**: Curves grow during training
3. **Ideal Region**: Show balanced loss zone
4. **Anomaly Indicators**: Highlight mode collapse or divergence
5. **Legend**: Clear G vs D labels

**Generated Output Gallery**:
1. **Output Grid**: 4x4 or similar grid of generated images
2. **Epoch Slider**: Jump to different training stages
3. **Animation Mode**: Watch outputs evolve over training
4. **Quality Indicator**: Rough measure of output quality

**Training Controls**:
1. **Train Button**: Start/pause training
2. **Step Mode**: One training step at a time
3. **Speed Control**: Fast/slow simulation
4. **Reset**: Start from scratch
5. **Epoch Counter**: Current training iteration

**Balance Visualization**:
1. **Tug-of-War Visual**: Two forces pulling (G vs D)
2. **Strength Indicator**: Who's currently winning
3. **Equilibrium Marker**: Ideal balanced state
4. **Seesaw Animation**: Show back-and-forth dynamics

**Mode Collapse Demo**:
1. **Collapse Preset**: Configuration that leads to mode collapse
2. **Output Diversity**: Show all outputs looking the same
3. **Detection Indicator**: Warning when collapse detected
4. **Fix Suggestions**: Techniques to address

**Real Data Comparison**:
1. **Real Samples Panel**: Show actual training data
2. **Side-by-Side**: Compare real vs generated
3. **Similarity Score**: How close generated is to real

**Visual Design Requirements**:
- Clear two-player visual metaphor
- Smooth loss curve rendering
- Image grid with clear boundaries
- Dynamic tug-of-war visualization
- Training phase highlighting

**Code Architecture Requirements**:
- GAN training simulation (or real TF.js training)
- Loss history tracking
- Output storage at checkpoints
- Animation and replay system
- Mode collapse detection heuristics

**Deliverables**:
Complete TypeScript implementation with architecture view, loss dynamics, output evolution, and training controls.
```
