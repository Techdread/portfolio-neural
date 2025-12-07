# I4: Correlation and Covariance — Three.js Visualization Prompt

## Visualization ID
I4

## Title
Correlation and Covariance

## Description
Drag points to change correlation, see covariance matrix, eigenvectors.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: I4
**Title**: Correlation and Covariance
**Description**: Drag points to change correlation, see covariance matrix, eigenvectors.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands mean, variance, and scatter plots

**Learning Objectives the visualization must support**:
1. See correlation in scatter plot shape
2. Watch covariance matrix update with data
3. See eigenvectors as principal directions
4. Understand correlation coefficient meaning

**Required Interactive Features**:

**Scatter Plot View**:
1. **Data Points**: Draggable 2D points
2. **Add Points**: Click to add new points
3. **Drag Points**: Move existing points
4. **Delete Points**: Remove points
5. **Clear All**: Reset data

**Data Generation**:
1. **Correlation Slider**: Set target correlation (-1 to 1)
2. **Generate Data**: Create points with specified correlation
3. **Sample Size**: How many points to generate
4. **Add Noise**: Scatter points with noise slider

**Statistics Display**:
1. **Correlation Coefficient**: Live r value (-1 to 1)
2. **Covariance Value**: Cov(X,Y)
3. **Individual Variances**: Var(X), Var(Y)
4. **Mean Point**: Show (μₓ, μᵧ) marker

**Covariance Matrix Panel**:
1. **2x2 Matrix Display**: Visual matrix with values
2. **Live Update**: Values change as points move
3. **Element Highlighting**: Hover to see which statistic
4. **Matrix Interpretation**: Labels for variance/covariance cells

**Eigenvector Visualization**:
1. **Eigenvector Arrows**: Two arrows from center
2. **Eigenvalue Display**: Length proportional to eigenvalue
3. **Principal Direction Labels**: PC1, PC2
4. **Toggle Eigenvectors**: Show/hide

**Ellipse Visualization**:
1. **Covariance Ellipse**: Ellipse fitting the data
2. **Ellipse Axes**: Aligned with eigenvectors
3. **1σ, 2σ, 3σ Ellipses**: Multiple confidence regions
4. **Toggle Ellipse**: Show/hide

**Correlation Presets**:
1. **Strong Positive (r ≈ 0.9)**: Tight upward slope
2. **Strong Negative (r ≈ -0.9)**: Tight downward slope
3. **No Correlation (r ≈ 0)**: Circular cloud
4. **Perfect (r = 1)**: Points on a line

**Comparison Mode**:
1. **Side-by-Side Plots**: Two datasets
2. **Same Correlation, Different Data**: Show sampling variability
3. **Different Correlations**: Compare relationships

**PCA Preview**:
1. **Project onto PC1**: Show 1D projection
2. **Variance Explained**: Percentage by first eigenvector
3. **Reconstruction**: Project and reconstruct

**Visual Design Requirements**:
- Clear scatter plot grid
- Draggable point interactions
- Smooth ellipse rendering
- Prominent eigenvector arrows
- Live-updating statistics

**Code Architecture Requirements**:
- Statistics computation (mean, variance, covariance)
- Eigenvector/eigenvalue computation for 2x2
- Ellipse rendering from covariance matrix
- Interactive point manipulation
- Real-time updates on data change

**Deliverables**:
Complete TypeScript implementation with interactive scatter plot, covariance matrix display, eigenvector visualization, and correlation exploration.
```
