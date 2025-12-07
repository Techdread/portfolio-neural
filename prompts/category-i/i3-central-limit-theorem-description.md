# I3: Central Limit Theorem Demo — Educational Explanation Prompt

## Topic
The Central Limit Theorem — Why the Gaussian is Everywhere

## Context
This is part of an interactive Three.js visualization portfolio. The learner will watch sum of any distribution converging to Gaussian.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: The Central Limit Theorem — Why the Gaussian is Everywhere

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will watch sum of any distribution converging to Gaussian.

**Prerequisites the learner should already understand**:
- Probability distributions (I1)
- Gaussian distribution basics
- What mean and variance are

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand CLT: sums of random variables become Gaussian
2. See that the original distribution doesn't matter (with conditions)
3. Know the rule: mean = sum of means, variance = sum of variances
4. Understand why Gaussian appears everywhere in nature
5. Connect to practical applications

**Required Sections**:
1. **The Surprising Fact** — Add up random variables, you get a bell curve (almost always)
2. **The Statement**:
   - Take any distribution (finite mean and variance)
   - Sum many independent samples
   - The sum's distribution approaches Gaussian
   - "Many" ≈ 30+ usually sufficient
3. **Visual Intuition**:
   - Sum of uniform → Gaussian
   - Sum of exponential → Gaussian
   - Sum of any → Gaussian
   - Only need mean and variance to predict result
4. **Parameters of the Limit**:
   - Mean of sum = n × original mean
   - Variance of sum = n × original variance
   - Standard deviation = √n × original std dev
5. **Why Does This Happen?**:
   - Extreme values cancel out
   - Central tendency reinforced
   - Mathematical proof beyond scope, but intuition is averaging
6. **Why Gaussian is Everywhere**:
   - Many natural quantities are sums of many factors
   - Height = sum of genetic + environmental factors
   - Measurement error = sum of many small errors
7. **Conditions and Exceptions**:
   - Requires finite variance (Cauchy doesn't converge)
   - Independence (or weak dependence)
8. **Why This Matters for ML/AI**:
   - Justifies Gaussian assumptions in many models
   - Batch statistics in batch normalization
   - Weight initialization theory
   - Confidence intervals and hypothesis testing

**Tone**: Focus on the "magic" of convergence. Make it feel like discovering a universal law.

**Length**: Approximately 1500-1900 words with clear examples of convergence.
```
