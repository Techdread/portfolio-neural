# Category I: Probability & Statistics — LLM Prompts

> **Target Audience**: Software developers with limited mathematics background  
> **Tech Stack**: Three.js, TypeScript  
> **Complexity**: Polished, production-quality code  
> **Purpose**: Educational portfolio demonstrating ML/AI concepts visually

---

## I1: Probability Distributions

### I1 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Probability Distributions — The Shapes of Randomness

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will explore interactive normal, uniform, and binomial distributions with parameter sliders that shift their shapes.

**Prerequisites the learner should already understand**:
- Basic probability (things happening with some chance)
- What a histogram shows
- Basic arithmetic

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand what a probability distribution represents
2. Know the uniform distribution and when it applies
3. Know the normal (Gaussian) distribution and its parameters
4. Know the binomial distribution for counting successes
5. Connect distributions to their use in ML

**Required Sections**:
1. **What is a Probability Distribution?**:
   - Describes how likely different outcomes are
   - PDF (continuous) vs PMF (discrete)
   - Area under curve = probability
2. **Uniform Distribution**:
   - All outcomes equally likely
   - Parameters: min, max
   - Examples: dice roll, random number generator
   - Shape: flat rectangle
3. **Normal (Gaussian) Distribution**:
   - The famous "bell curve"
   - Parameters: mean (μ) and standard deviation (σ)
   - Mean = center of the bell
   - Std dev = width of the bell
   - 68-95-99.7 rule (1σ, 2σ, 3σ)
   - Central Limit Theorem: many things become normal
4. **Binomial Distribution**:
   - Count of successes in n trials
   - Parameters: n (trials), p (probability)
   - Examples: coin flips, clicks, conversions
   - Discrete: only integer values
5. **Other Important Distributions** (brief mention):
   - Poisson: count of rare events
   - Exponential: time between events
   - Beta: probabilities of probabilities
6. **Why This Matters for ML/AI**:
   - Data often assumed to follow distributions
   - Weight initialization uses normal distribution
   - Noise modeling (sensor noise is often normal)
   - Understanding uncertainty and confidence intervals
   - Probabilistic models, Bayesian methods

**Tone**: Make distributions feel intuitive. Use real-world examples heavily.

**Length**: Approximately 1800-2200 words covering the three main distributions thoroughly.
```

### I1 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: I1
**Title**: Probability Distributions
**Description**: Interactive normal, uniform, binomial. Parameter sliders shift shape.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic probability concepts

**Learning Objectives the visualization must support**:
1. See distribution shapes clearly
2. Understand how parameters change shape
3. Compare different distributions
4. Sample from distributions interactively

**Required Interactive Features**:

**Distribution Selector**:
1. **Tabs or Buttons**: Uniform, Normal, Binomial
2. **Currently Selected**: Clear highlight
3. **Quick Compare**: Button to overlay all three

**Distribution Plot**:
1. **PDF/PMF Curve**: Smooth curve (continuous) or bars (discrete)
2. **X-Axis Range**: Appropriate for distribution
3. **Y-Axis**: Probability density/mass
4. **Filled Area**: Shaded under curve
5. **Grid Lines**: Reference lines

**Parameter Controls**:
1. **Uniform Distribution**:
   - Min slider (a)
   - Max slider (b)
   - Display: "Uniform(a, b)"
2. **Normal Distribution**:
   - Mean slider (μ): range -5 to 5
   - Std Dev slider (σ): range 0.1 to 3
   - Display: "Normal(μ, σ²)"
3. **Binomial Distribution**:
   - Trials slider (n): 1 to 100
   - Probability slider (p): 0 to 1
   - Display: "Binomial(n, p)"

**Statistics Display**:
1. **Mean**: Expected value
2. **Variance**: Spread measure
3. **Standard Deviation**: √Variance
4. **Mode**: Most likely value
5. **Update Live**: Values change with sliders

**Sampling Demo**:
1. **Sample Button**: Draw samples from distribution
2. **Sample Count**: How many samples to draw
3. **Histogram Overlay**: Show empirical distribution
4. **Sample Points**: Animate samples appearing
5. **Convergence**: Watch histogram approach true distribution

**Probability Calculator**:
1. **Range Selection**: Drag to select x-range
2. **Probability Display**: P(a < X < b)
3. **Shaded Region**: Highlight selected area
4. **CDF Option**: Show cumulative distribution

**Comparison Mode**:
1. **Multiple Distributions**: Overlay 2-3 distributions
2. **Color Coding**: Distinct colors for each
3. **Parameter Matching**: Same mean, different shapes
4. **Legend**: Which distribution is which

**Visual Design Requirements**:
- Smooth, mathematically accurate curves
- Clear axis labels and tick marks
- Interactive highlighting on hover
- Animated parameter changes
- Professional color scheme

**Code Architecture Requirements**:
- Distribution classes (PDF, CDF, sampling, stats)
- High-resolution curve rendering
- Efficient histogram computation
- Interactive range selection
- Parameter binding for live updates

**Deliverables**:
Complete TypeScript implementation with distribution plots, parameter controls, sampling, and comparison mode.
```

---

## I2: Bayes' Theorem

### I2 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Bayes' Theorem — Updating Beliefs with Evidence

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see visual area diagrams showing prior → evidence → posterior updates.

**Prerequisites the learner should already understand**:
- Basic probability (what a probability means)
- Conditional probability (P(A|B) = probability of A given B)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand Bayes' theorem formula and meaning
2. Know what prior, likelihood, and posterior mean
3. Visualize probability updates with area diagrams
4. Apply Bayes' theorem to simple problems
5. Connect to Bayesian machine learning

**Required Sections**:
1. **The Updating Problem** — How should we change beliefs when we get new evidence?
2. **The Formula**:
   - P(H|E) = P(E|H) × P(H) / P(E)
   - Posterior = Likelihood × Prior / Evidence
3. **The Players**:
   - Prior P(H): What we believed before evidence
   - Likelihood P(E|H): How likely evidence is if H is true
   - Posterior P(H|E): Updated belief after seeing evidence
   - Evidence P(E): Total probability of evidence
4. **Intuitive Example**:
   - Medical test example (disease diagnosis)
   - Walk through with actual numbers
   - Show why intuition often fails (base rate neglect)
5. **Visual Area Interpretation**:
   - Total area = 1 (all possibilities)
   - Prior = relative sizes of hypothesis regions
   - Evidence = subset that matches observation
   - Posterior = proportion within evidence subset
6. **Sequential Updates** — Apply Bayes repeatedly as evidence arrives
7. **Why This Matters for ML/AI**:
   - Bayesian neural networks
   - Naive Bayes classifier
   - Probabilistic programming
   - Uncertainty quantification
   - Belief updating is fundamental to intelligence

**Tone**: Use a concrete example throughout (medical test is classic). Make the formula feel intuitive.

**Length**: Approximately 1700-2100 words with worked numerical example.
```

### I2 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: I2
**Title**: Bayes' Theorem Visualiser
**Description**: Visual area diagrams: prior → evidence → posterior.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands basic probability

**Learning Objectives the visualization must support**:
1. See prior probabilities as areas
2. Watch evidence update beliefs
3. Understand likelihood and posterior visually
4. Work through examples interactively

**Required Interactive Features**:

**Scenario Setup**:
1. **Preset Scenarios**:
   - Medical test (disease diagnosis)
   - Spam filter (email classification)
   - Weather prediction (rain given clouds)
   - Custom scenario
2. **Hypothesis Definition**: What we're trying to determine (H, not H)
3. **Evidence Definition**: What observation we made (E)

**Prior Probability View**:
1. **Area Diagram**: Rectangle split by prior P(H) vs P(not H)
2. **Prior Slider**: Adjust P(H) from 0.01 to 0.99
3. **Size Animation**: Regions resize with slider
4. **Label Display**: "P(Disease) = 0.01"

**Likelihood Input**:
1. **P(E|H) Slider**: Evidence probability if hypothesis true
2. **P(E|not H) Slider**: Evidence probability if hypothesis false
3. **Interpretation Labels**: "Test sensitivity" / "False positive rate"

**Evidence Visualization**:
1. **Highlight Evidence Region**: Show E within each hypothesis region
2. **E|H Shading**: Part of H where evidence occurred
3. **E|not H Shading**: Part of not H where evidence occurred
4. **Total Evidence**: P(E) = P(E|H)P(H) + P(E|not H)P(not H)

**Posterior Calculation**:
1. **Step-by-Step Animation**:
   - Start with prior areas
   - Show likelihood shading
   - Zoom into evidence region
   - Calculate relative proportions
2. **Formula Display**: Show Bayes formula with current values
3. **Result**: P(H|E) prominently displayed
4. **Surprise Indicator**: How much belief changed

**Interactive Area Diagram**:
1. **Full Rectangle**: 100% of possibilities
2. **H / not H Columns**: Prior split
3. **E / not E Rows**: Evidence split
4. **Four Quadrants**: H∩E, H∩notE, notH∩E, notH∩notE
5. **Hover Info**: Show probability of each region
6. **Posterior Highlight**: The relevant ratio (H∩E / E)

**Sequential Updates**:
1. **Multiple Evidence Button**: Apply Bayes repeatedly
2. **Prior Becomes Posterior**: Each update feeds into next
3. **Belief Trajectory**: Show how belief changes with evidence
4. **Convergence Demo**: Many observations → confident posterior

**Counter-Intuitive Example**:
1. **Base Rate Neglect Demo**: Rare disease, accurate test
2. **Intuition Input**: "What do you think P(disease|positive) is?"
3. **Actual Answer**: Show surprisingly low posterior
4. **Explanation**: Why prior matters so much

**Visual Design Requirements**:
- Clean area diagrams with clear boundaries
- Color coding (H = blue, not H = orange)
- Smooth transitions when parameters change
- Clear formula display with substituted values
- Intuitive quadrant layout

**Code Architecture Requirements**:
- Bayes calculation functions
- Area diagram rendering (rectangles with subdivision)
- Animation system for transitions
- Scenario presets with parameters
- Sequential update state management

**Deliverables**:
Complete TypeScript implementation with area visualization, parameter controls, step-by-step calculation, and sequential updates.
```

---

## I3: Maximum Likelihood

### I3 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Maximum Likelihood Estimation — Finding the Best Parameters

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will explore finding parameters that make observed data most probable.

**Prerequisites the learner should already understand**:
- Probability distributions (I1)
- What parameters are (like μ and σ)
- Basic optimization concept (finding best value)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand likelihood as probability of data given parameters
2. Know the maximum likelihood principle
3. See MLE as an optimization problem
4. Understand log-likelihood and why it's used
5. Connect MLE to training neural networks

**Required Sections**:
1. **The Estimation Problem** — Given data, what parameters generated it?
2. **Likelihood Function**:
   - L(θ) = P(data | parameters θ)
   - "How probable is this data if parameters are θ?"
   - NOT P(parameters | data) — that's Bayesian
3. **Maximum Likelihood Principle**:
   - Choose θ that maximizes L(θ)
   - "Find parameters that make data most likely"
4. **Simple Example: Coin Flipping**:
   - Data: 7 heads, 3 tails
   - Parameter: p (probability of heads)
   - Likelihood: p⁷(1-p)³
   - MLE: p = 0.7
5. **Log-Likelihood**:
   - Products → sums (numerically stable)
   - log L = Σ log P(xᵢ | θ)
   - Maximizing log L = maximizing L
6. **MLE for Normal Distribution**:
   - MLE of μ = sample mean
   - MLE of σ² = sample variance
7. **Connection to Loss Functions**:
   - Negative log-likelihood = cross-entropy loss!
   - Minimizing cross-entropy = maximizing likelihood
   - Training neural networks = MLE (often)
8. **Why This Matters for ML/AI**:
   - Foundation of statistical learning
   - Explains why we minimize cross-entropy
   - Bridge between probability and optimization

**Tone**: Focus on the intuition of "making data likely." The coin example is crucial.

**Length**: Approximately 1600-2000 words with clear examples and ML connection.
```

### I3 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: I3
**Title**: Maximum Likelihood Estimation
**Description**: Find parameters making observed data most probable.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands probability distributions

**Learning Objectives the visualization must support**:
1. See likelihood as function of parameters
2. Watch MLE optimization find best parameters
3. Understand how data shapes the likelihood
4. See connection to distribution fitting

**Required Interactive Features**:

**Data Generation**:
1. **Sample Data Points**: Generate or input data
2. **True Parameters** (hidden/revealed): Parameters that generated data
3. **Data Display**: Scatter plot or histogram of samples
4. **Sample Size Control**: N = 10, 50, 100, 500

**Scenario Selector**:
1. **Coin Flipping**: Binomial, estimate p
2. **Normal Distribution**: Estimate μ (known σ)
3. **Normal Distribution**: Estimate μ and σ
4. **Linear Regression**: Estimate slope and intercept (as MLE)

**Likelihood Function Plot**:
1. **1D Case (single parameter)**:
   - X-axis: parameter value
   - Y-axis: likelihood (or log-likelihood)
   - Curve showing L(θ)
   - Peak = MLE
2. **2D Case (two parameters)**:
   - Contour plot or 3D surface
   - X-axis: parameter 1
   - Y-axis: parameter 2
   - Height/color: likelihood
   - Peak location = MLE

**Parameter Exploration**:
1. **Parameter Slider**: Manually adjust parameter
2. **Likelihood Value**: Display L(θ) at current setting
3. **Data Probability**: Show how likely each point is
4. **Product Visualization**: See likelihoods multiplying

**MLE Optimizer**:
1. **Find MLE Button**: Run optimization
2. **Animation**: Watch parameter move to peak
3. **Gradient Path**: Show optimization trajectory
4. **Final Estimate**: Display MLE value

**Fit Visualization**:
1. **Distribution Overlay**: Show distribution with current parameters
2. **Fit Quality**: Visual of how well distribution matches data
3. **MLE vs True**: Compare estimated to true (if known)
4. **Histogram Comparison**: Data histogram vs fitted distribution

**Log-Likelihood Toggle**:
1. **Likelihood View**: Product of probabilities
2. **Log-Likelihood View**: Sum of log probabilities
3. **Numerical Values**: Show why log is more stable

**Sample Size Effect**:
1. **N Slider**: Change number of data points
2. **Likelihood Sharpness**: Peak gets sharper with more data
3. **MLE Variance**: Estimate more precise with more data
4. **Convergence Demo**: Watch MLE approach true value

**Visual Design Requirements**:
- Clear likelihood curves/surfaces
- Data points visible
- Parameter indicator on curve
- Peak marking for MLE
- Smooth optimization animation

**Code Architecture Requirements**:
- Likelihood computation for various distributions
- Numerical optimization (gradient ascent or grid search)
- Plot rendering (1D curves, 2D contours)
- Data generation from distributions
- Animation system for optimizer

**Deliverables**:
Complete TypeScript implementation with likelihood visualization, parameter exploration, MLE optimization, and fit comparison.
```

---

## I4: Information Theory Basics

### I4 — Educational Explanation Prompt

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Information Theory — Entropy and KL Divergence

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will visualize entropy and KL divergence with interactive distributions.

**Prerequisites the learner should already understand**:
- Probability distributions (I1)
- Logarithms (basic understanding)
- What "uncertainty" means informally

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand entropy as a measure of uncertainty
2. Know the formula for entropy and its meaning
3. Understand KL divergence as distance between distributions
4. See why cross-entropy is used as loss function
5. Connect information theory to machine learning

**Required Sections**:
1. **Information and Surprise**:
   - Rare events carry more information
   - Information = -log(probability)
   - Bits of information
2. **Entropy Definition**:
   - H(P) = -Σ P(x) log P(x)
   - Average information/surprise
   - Measures uncertainty in distribution
3. **Entropy Examples**:
   - Fair coin: H = 1 bit (maximum uncertainty)
   - Biased coin (99% heads): H ≈ 0.08 bits (low uncertainty)
   - Uniform distribution: maximum entropy
   - Peaked distribution: low entropy
4. **Cross-Entropy**:
   - H(P, Q) = -Σ P(x) log Q(x)
   - Using Q's code to encode P's messages
   - Always ≥ entropy of P
5. **KL Divergence**:
   - D_KL(P || Q) = Σ P(x) log(P(x) / Q(x))
   - "Distance" from Q to P (not symmetric!)
   - = Cross-entropy - Entropy
   - Measures how different two distributions are
6. **Why This Matters for ML/AI**:
   - Cross-entropy loss = we want model Q to match true P
   - KL divergence in VAEs
   - Information bottleneck
   - Understanding model uncertainty
7. **Connection to Classification**:
   - True label = P (one-hot)
   - Model output = Q (softmax)
   - Cross-entropy loss minimizes KL divergence!

**Tone**: Make entropy feel like "unpredictability" or "surprise." Information theory should feel applicable, not abstract.

**Length**: Approximately 1800-2200 words with clear examples and ML connections.
```

### I4 — Three.js Visualization Prompt

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: I4
**Title**: Information Theory Basics
**Description**: Entropy, KL divergence visualised with distributions.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands probability distributions

**Learning Objectives the visualization must support**:
1. See entropy as measure of distribution spread
2. Compare distributions via KL divergence
3. Understand cross-entropy visually
4. Connect to ML loss functions

**Required Interactive Features**:

**Entropy Visualization**:
1. **Distribution P**: Bar chart for discrete distribution (4-8 outcomes)
2. **Probability Sliders**: Adjust each P(x) (auto-normalize to sum=1)
3. **Entropy Display**: H(P) computed and displayed prominently
4. **Entropy Bar**: Visual indicator (0 to max entropy)
5. **Preset Distributions**:
   - Uniform (max entropy)
   - Peaked (low entropy)
   - Bimodal

**Per-Outcome Information**:
1. **Information Values**: Show -log P(x) for each outcome
2. **Bar Heights**: Visualize information per outcome
3. **Weighted Average**: Show entropy as weighted average
4. **Hover Details**: Click outcome to see its contribution

**KL Divergence View**:
1. **Two Distributions**: P (true) and Q (model)
2. **Side-by-Side Display**: Both distributions visible
3. **Q Adjustable**: Sliders to modify Q
4. **KL Divergence Display**: D_KL(P || Q) computed
5. **Asymmetry Demo**: Show D_KL(P||Q) ≠ D_KL(Q||P)

**Cross-Entropy Breakdown**:
1. **H(P, Q) Display**: Cross-entropy value
2. **Components**: Show H(P, Q) = H(P) + D_KL(P || Q)
3. **Visual Equation**: Interactive formula with values
4. **Minimization Goal**: "Make Q match P"

**Distribution Matching Game**:
1. **Target P**: Given true distribution
2. **Adjust Q**: User modifies Q to match P
3. **KL Score**: Real-time KL divergence feedback
4. **Success Indicator**: KL = 0 when Q = P
5. **Leaderboard**: Best match achieved

**Gradient Visualization**:
1. **KL Gradient w.r.t. Q**: Show how to adjust Q to reduce KL
2. **Optimization Animation**: Watch Q approach P
3. **Cross-Entropy Descent**: Animate loss minimization

**ML Connection Panel**:
1. **Classification Setup**: True class as one-hot P
2. **Model Output**: Softmax probabilities as Q
3. **Cross-Entropy Loss**: Show it's exactly H(P, Q)
4. **Training Interpretation**: "Minimize KL from true to predicted"

**Entropy Comparisons**:
1. **Multiple Distributions**: Compare entropy of different shapes
2. **Ranking**: Order by entropy
3. **Intuition Builder**: "Which is more uncertain?"

**Visual Design Requirements**:
- Clear bar charts for distributions
- Entropy/KL values prominently displayed
- Color coding (P = blue, Q = orange)
- Interactive sliders with immediate feedback
- Formula display with live values

**Code Architecture Requirements**:
- Entropy calculation function
- Cross-entropy calculation
- KL divergence calculation
- Distribution normalization
- Gradient computation for optimization

**Deliverables**:
Complete TypeScript implementation with entropy visualization, KL divergence comparison, cross-entropy breakdown, and ML connection demo.
```

---

## Summary

| ID | Title | Education Prompt | Visualization Prompt |
|----|-------|------------------|---------------------|
| I1 | Probability Distributions | ✅ | ✅ |
| I2 | Bayes' Theorem | ✅ | ✅ |
| I3 | Maximum Likelihood | ✅ | ✅ |
| I4 | Information Theory Basics | ✅ | ✅ |
