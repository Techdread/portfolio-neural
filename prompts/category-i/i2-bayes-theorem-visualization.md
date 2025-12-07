# I2: Bayes' Theorem Visualised — Three.js Visualization Prompt

## Visualization ID
I2

## Title
Bayes' Theorem Visualised

## Description
Prior → evidence → posterior. Watch belief update.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: I2
**Title**: Bayes' Theorem Visualised
**Description**: Prior → evidence → posterior. Watch belief update.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic probability and distributions

**Learning Objectives the visualization must support**:
1. See prior belief as a distribution
2. See how evidence modifies belief
3. Watch posterior emerge from combination
4. Understand sequential updates

**Required Interactive Features**:

**Pipeline View**:
1. **Three-Stage Display**: Prior → Likelihood → Posterior
2. **Flow Arrows**: Data flow direction
3. **Current Stage Highlight**: Which component is active

**Prior Distribution**:
1. **Prior Plot**: Distribution over hypothesis parameter
2. **Prior Shape Selector**: Uniform, Beta, Gaussian
3. **Prior Parameters**: Sliders to adjust shape
4. **Belief Interpretation**: "Before seeing data, we believe..."

**Likelihood Display**:
1. **Evidence Input**: What observation was made
2. **Likelihood Function**: P(Evidence | Parameter)
3. **Likelihood Plot**: How likely is evidence for each parameter value
4. **Evidence Selector**: Different possible observations

**Posterior Distribution**:
1. **Posterior Plot**: Updated belief after evidence
2. **Animation**: Watch prior "morph" into posterior
3. **Posterior Stats**: Mean, mode, credible interval
4. **Comparison Overlay**: Prior vs posterior on same axes

**Classic Examples**:
1. **Coin Flipping**: Prior on coin bias, observe flips
2. **Medical Testing**: Disease prevalence, test result
3. **Custom Scenario**: User-defined prior and likelihood

**Sequential Update Demo**:
1. **Multiple Evidence Button**: Add more data points
2. **Sequential Animation**: Watch posterior update repeatedly
3. **Data Points Display**: List of all observations
4. **Convergence**: Watch belief sharpen with more data

**Formula Display**:
1. **Bayes' Formula**: Show P(H|E) = P(E|H)P(H)/P(E)
2. **Value Substitution**: Plug in current values
3. **Step-by-Step Calculation**: Expand each term

**Interactive Exploration**:
1. **Drag Prior**: Click and drag to reshape prior
2. **Instant Posterior Update**: See posterior change immediately
3. **Evidence Strength Slider**: Strong vs weak evidence

**Visual Design Requirements**:
- Smooth distribution curves
- Clear before/after comparison
- Animated transitions for updates
- Color coding (prior = blue, likelihood = green, posterior = purple)
- Formula rendering

**Code Architecture Requirements**:
- Distribution classes with Bayesian update methods
- Prior × Likelihood = Posterior computation
- Sequential update state management
- Animation for distribution morphing
- Multiple example scenarios

**Deliverables**:
Complete TypeScript implementation with prior/posterior visualization, sequential updates, classic examples, and formula display.
```
