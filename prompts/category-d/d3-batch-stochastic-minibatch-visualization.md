# D3: Batch vs Stochastic vs Mini-batch — Three.js Visualization Prompt

## Visualization ID
D3

## Title
Batch vs Stochastic vs Mini-batch

## Description
Gradient estimate noise/accuracy differences affecting descent path.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: D3
**Title**: Batch vs Stochastic vs Mini-batch
**Description**: Gradient estimate noise/accuracy differences affecting descent path.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands gradient descent

**Learning Objectives the visualization must support**:
1. See smooth path with batch GD
2. See noisy path with stochastic GD
3. See moderate noise with mini-batch
4. Understand trade-off between accuracy and speed

**Required Interactive Features**:

**Dataset View**:
1. **Data Points**: Scatter plot of synthetic data (e.g., 100-500 points)
2. **Model Line/Curve**: Current model prediction
3. **Individual Losses**: Option to show loss per data point

**Gradient Descent Comparison**:
1. **Three Simultaneous Runs**:
   - Batch (all data): smooth path
   - Stochastic (1 sample): noisy path
   - Mini-batch (configurable): moderate noise
2. **Color-Coded Paths**: Distinct colors for each variant
3. **Same Starting Point**: Fair comparison

**Loss Surface View**:
1. **2D Parameter Space**: Contour plot
2. **True Loss Surface**: Based on full dataset
3. **Estimated Gradient Arrows**: Show gradient estimate for each variant
4. **Gradient Noise Visualization**: Show how estimated gradients vary

**Batch Size Control**:
1. **Mini-batch Size Slider**: 1 (SGD) to full dataset (batch)
2. **Real-Time Path Update**: See path change with batch size
3. **Current Sample Highlight**: Show which samples are being used

**Speed vs Accuracy Panel**:
1. **Steps per Second**: Show update frequency
2. **Gradient Variance**: Show noise level
3. **Time to Convergence**: Estimated time comparison

**Noise Benefits Demo**:
1. **Local Minimum Surface**: Surface with trap
2. **Watch SGD Escape**: Noise helps jump out
3. **Batch Gets Stuck**: Smooth path goes into trap

**Animation Controls**:
1. **Play/Pause/Step**: Standard controls
2. **Speed Control**: Adjust animation speed
3. **Reset**: Return to start

**Visual Design Requirements**:
- Data points clearly visible
- Paths with different dash patterns or colors
- Gradient arrows showing direction and magnitude
- Noise level indicator (maybe oscillation amplitude)
- Clear legend

**Code Architecture Requirements**:
- Synthetic data generator
- Loss computation with sample subsets
- Gradient estimation with configurable batch size
- Path rendering with noise visualization
- Comparison metrics tracking

**Deliverables**:
Complete TypeScript implementation with data view, three-way comparison, batch size control, and noise benefit demonstration.
```
