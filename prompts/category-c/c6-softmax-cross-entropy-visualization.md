# C6: Softmax & Cross-Entropy — Three.js Visualization Prompt

## Visualization ID
C6

## Title
Softmax & Cross-Entropy

## Description
Logits → probabilities → loss. Show harsh penalty for confident wrong predictions.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: C6
**Title**: Softmax & Cross-Entropy
**Description**: Logits → probabilities → loss. Show harsh penalty for confident wrong predictions.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands probability basics
- User understands loss concepts (C5)

**Learning Objectives the visualization must support**:
1. See logits transform to probabilities via softmax
2. Watch probabilities become loss via cross-entropy
3. Understand the harsh penalty for confident wrong predictions
4. Explore temperature effects on softmax

**Required Interactive Features**:

**Pipeline View**:
1. **Logits Input**: Sliders for 3-5 class logits
2. **Softmax Step**: Visual transformation to probabilities
3. **Probability Bars**: Bar chart of output probabilities
4. **True Class Selector**: Pick which class is correct
5. **Cross-Entropy Calculation**: Show -log(p_correct) computation
6. **Final Loss Display**: Large, prominent loss value

**Softmax Exploration**:
1. **Individual Logit Sliders**: Change each independently
2. **Probability Response**: Watch probabilities shift
3. **Dominant Class Highlight**: Show which class "wins"
4. **Relative Difference Demo**: Show that only relative differences matter (subtract constant)

**Cross-Entropy Deep Dive**:
1. **Probability vs Loss Curve**: Plot -log(p) for p from 0 to 1
2. **Current Point Marker**: Show where current prediction sits on curve
3. **Harsh Penalty Zone**: Highlight region where loss explodes (p near 0)
4. **Confidence Slider**: Drag prediction probability, watch loss change

**Confident & Wrong Demo**:
1. **Scenario Presets**:
   - Confident correct: high prob on true class
   - Uncertain: roughly equal probs
   - Confident wrong: high prob on wrong class
2. **Loss Comparison**: Show dramatic difference in loss values
3. **Gradient Display**: Show how gradients differ in each case

**Temperature Control**:
1. **Temperature Slider**: τ from 0.1 to 10
2. **Effect Visualization**: Watch probability distribution sharpen or flatten
3. **Extreme Cases**: Near 0 → one-hot, high → uniform

**Visual Design Requirements**:
- Pipeline flowing left to right
- Bar charts for probabilities
- Loss value prominently displayed with color coding (red = high)
- -log(p) curve clearly plotted
- Smooth animations when logits change

**Code Architecture Requirements**:
- Softmax function with temperature
- Cross-entropy calculation
- Gradient computation (for display)
- Responsive bar chart rendering
- Animation for transitions

**Deliverables**:
Complete TypeScript implementation with interactive pipeline, probability visualization, and cross-entropy exploration.
```
