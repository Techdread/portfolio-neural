# I1: Probability Distributions — Educational Explanation Prompt

## Topic
Probability Distributions — The Language of Uncertainty

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see interactive Gaussian, uniform, and categorical distributions with sampling visualization.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Probability Distributions — The Language of Uncertainty

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see interactive Gaussian, uniform, and categorical distributions with sampling visualization.

**Prerequisites the learner should already understand**:
- Basic probability (what probability means)
- What a function is
- Basic statistics (mean, variance idea)

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand probability distributions as descriptions of random outcomes
2. Know continuous vs discrete distributions
3. Understand Gaussian (normal) distribution and its parameters
4. Know uniform and categorical distributions
5. See how sampling works

**Required Sections**:
1. **What is a Probability Distribution?** — Describes which outcomes are likely/unlikely
2. **Discrete vs Continuous**:
   - Discrete: countable outcomes (dice roll, categories)
   - Continuous: any value in a range (height, temperature)
3. **Uniform Distribution**:
   - All outcomes equally likely
   - Discrete: fair die
   - Continuous: random point in interval
4. **Categorical Distribution**:
   - Fixed set of categories with probabilities
   - Probabilities sum to 1
   - Generalization of coin flip
5. **Gaussian (Normal) Distribution**:
   - The famous bell curve
   - Parameters: mean (μ) = center, variance (σ²) = spread
   - 68-95-99.7 rule
   - Central limit theorem: sums become Gaussian
6. **Probability Density vs Mass**:
   - PMF for discrete: probability of exact value
   - PDF for continuous: probability of interval (area under curve)
7. **Sampling from Distributions**:
   - Random draws following the distribution
   - Histograms approximate the distribution
   - More samples = closer approximation
8. **Why This Matters for ML/AI**:
   - Weights initialized from distributions
   - Noise for regularization (dropout, data augmentation)
   - Probabilistic predictions (softmax = categorical)
   - VAEs: sampling from latent distribution
   - Bayesian methods throughout

**Tone**: Make probability feel intuitive, not intimidating. Use everyday examples (dice, heights, weather).

**Length**: Approximately 1800-2200 words covering the major distributions clearly.
```
