# I1: Probability Distributions — Three.js Visualization Prompt

## Visualization ID
I1

## Title
Probability Distributions

## Description
Interactive Gaussian, uniform, categorical distributions with sampling.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: I1
**Title**: Probability Distributions
**Description**: Interactive Gaussian, uniform, categorical distributions with sampling.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic probability concept

**Learning Objectives the visualization must support**:
1. See different distribution shapes
2. Understand parameters affect shape
3. Watch sampling in action
4. Connect histogram to distribution

**Required Interactive Features**:

**Distribution Selector**:
1. **Distribution Tabs**: Gaussian, Uniform, Categorical, Exponential
2. **Quick Switch**: Easy navigation between distributions
3. **Current Distribution Highlight**: Clear selection indicator

**Gaussian View**:
1. **Bell Curve**: Smooth PDF plot
2. **Mean Slider (μ)**: Move center left/right (-5 to 5)
3. **Std Dev Slider (σ)**: Adjust spread (0.5 to 3)
4. **68-95-99.7 Markers**: Show standard deviation regions
5. **Area Display**: Shade area for selected range

**Uniform View**:
1. **Flat PDF**: Rectangle plot
2. **Min Slider**: Adjust lower bound
3. **Max Slider**: Adjust upper bound
4. **Equal Probability Label**: Show constant height

**Categorical View**:
1. **Bar Chart**: Probability bars for each category
2. **Category Count Slider**: 2 to 10 categories
3. **Probability Sliders**: Adjust each category's probability
4. **Auto-Normalize**: Keep probabilities summing to 1
5. **Category Labels**: Name each category

**Sampling Visualization**:
1. **Sample Button**: Draw one sample
2. **Sample Many Button**: Draw N samples quickly
3. **Sample Count Slider**: How many to draw
4. **Sample Points**: Show samples on x-axis
5. **Histogram Build-Up**: Watch histogram form as samples accumulate
6. **Distribution Overlay**: Show true distribution over histogram
7. **Clear Samples**: Reset histogram

**Animation Mode**:
1. **Continuous Sampling**: Auto-draw samples over time
2. **Speed Control**: Slow to fast
3. **Sample Counter**: Total samples drawn
4. **Convergence Display**: Histogram approaching true distribution

**Statistics Panel**:
1. **Theoretical Mean**: μ for the distribution
2. **Theoretical Variance**: σ² for the distribution
3. **Sample Mean**: Mean of drawn samples
4. **Sample Variance**: Variance of drawn samples
5. **Convergence Indicator**: How close sample stats are to true

**Visual Design Requirements**:
- Smooth curve rendering for PDFs
- Clear bar charts
- Animated sample drops
- Histogram with adjustable bin count
- Color coding for different distributions

**Code Architecture Requirements**:
- Distribution classes with PDF/PMF and sample methods
- Histogram computation
- Animation loop for continuous sampling
- Statistics computation
- Parameter binding and updates

**Deliverables**:
Complete TypeScript implementation with multiple distributions, parameter controls, sampling visualization, and statistics display.
```
