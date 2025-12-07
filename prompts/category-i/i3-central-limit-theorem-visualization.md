# I3: Central Limit Theorem Demo — Three.js Visualization Prompt

## Visualization ID
I3

## Title
Central Limit Theorem Demo

## Description
Sum of any distribution converging to Gaussian.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: I3
**Title**: Central Limit Theorem Demo
**Description**: Sum of any distribution converging to Gaussian.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands probability distributions

**Learning Objectives the visualization must support**:
1. See original distribution (any shape)
2. Watch sum distribution evolve as n increases
3. See convergence to Gaussian
4. Verify with any starting distribution

**Required Interactive Features**:

**Source Distribution**:
1. **Distribution Selector**:
   - Uniform
   - Exponential
   - Bimodal (two peaks)
   - Discrete (dice)
   - Skewed
2. **Distribution Preview**: Show the original PDF/PMF
3. **Parameter Sliders**: Adjust distribution parameters

**Sample Size Control**:
1. **n Slider**: Number of samples to sum (1 to 100)
2. **Animate n Button**: Watch n increase over time
3. **Current n Display**: Prominent indicator

**Sum Distribution Display**:
1. **Histogram of Sums**: Distribution of summed samples
2. **Gaussian Overlay**: Theoretical limiting Gaussian
3. **Convergence Indicator**: How close to Gaussian
4. **Evolution Animation**: Watch histogram morph as n changes

**Sampling Visualization**:
1. **Sample Generation**: Show individual samples being drawn
2. **Sum Computation**: Animate summing samples together
3. **Sample Counter**: Total sum samples generated
4. **Continuous Sampling**: Keep drawing and updating histogram

**Comparison Panel**:
1. **Original vs Sum**: Side-by-side distributions
2. **Statistics Table**: Mean, variance for original and sum
3. **Theoretical vs Observed**: Compare computed mean/variance

**Multiple Starting Points**:
1. **Quick Compare**: Show several source distributions converging
2. **Grid Layout**: 2x2 or 3x3 comparison
3. **Same n for All**: Synchronized n slider
4. **All Converge**: Watch all approach Gaussian

**Interactive Exploration**:
1. **Click to Sample**: Manual sample generation
2. **Extreme Distribution Button**: Try a weird distribution
3. **n=1 vs n=30 Toggle**: Quick before/after

**Statistics Display**:
1. **CLT Prediction**: Expected mean = nμ, variance = nσ²
2. **Observed Statistics**: Computed from samples
3. **Error Metrics**: Difference from prediction

**Visual Design Requirements**:
- Clear histogram rendering
- Smooth Gaussian overlay curve
- Animated transitions as n changes
- Color coding for original vs sum
- Prominent n indicator

**Code Architecture Requirements**:
- Multiple distribution implementations
- Sum distribution computation
- Gaussian fit calculation
- Animation for n evolution
- Statistics computation

**Deliverables**:
Complete TypeScript implementation with distribution selector, n control, convergence animation, and comparison views.
```
