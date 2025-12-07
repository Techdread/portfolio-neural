# I2: Bayes' Theorem Visualised — Educational Explanation Prompt

## Topic
Bayes' Theorem — Updating Beliefs with Evidence

## Context
This is part of an interactive Three.js visualization portfolio. The learner will see the prior → evidence → posterior pipeline visually, experiencing belief updating.

---

```
You are creating educational content for a developer learning AI/ML who has a weak mathematics background.

**Topic**: Bayes' Theorem — Updating Beliefs with Evidence

**Context**: This is part of an interactive Three.js visualization portfolio. The learner will see the prior → evidence → posterior pipeline visually, experiencing belief updating.

**Prerequisites the learner should already understand**:
- Basic probability
- Probability distributions (I1)
- Conditional probability idea (P(A|B))

**Learning Objectives** — After reading this explanation, the learner should:
1. Understand Bayes' theorem as a belief update mechanism
2. Know the components: prior, likelihood, evidence, posterior
3. See how evidence changes beliefs
4. Understand the formula intuitively
5. Connect to ML applications

**Required Sections**:
1. **The Belief Update Problem** — We have beliefs, we see evidence, how should beliefs change?
2. **The Components**:
   - Prior P(H): initial belief before evidence
   - Likelihood P(E|H): probability of evidence if hypothesis true
   - Evidence P(E): overall probability of evidence
   - Posterior P(H|E): updated belief after evidence
3. **Bayes' Formula**:
   - P(H|E) = P(E|H) × P(H) / P(E)
   - Posterior ∝ Likelihood × Prior
4. **Intuitive Explanation**:
   - Start with prior belief
   - Evidence that's more likely under H increases belief in H
   - Normalize to get valid probability
5. **Classic Example: Medical Testing**:
   - Prior: disease prevalence
   - Likelihood: test sensitivity
   - Evidence: overall positive rate
   - Posterior: actual probability of disease given positive test
6. **Sequential Updates**:
   - Today's posterior = tomorrow's prior
   - Keep updating as evidence arrives
7. **Why This Matters for ML/AI**:
   - Bayesian inference and probabilistic models
   - Naive Bayes classifier
   - Bayesian neural networks
   - Thompson sampling in bandits
   - Prior/posterior in VAEs

**Tone**: Use the "belief update" framing heavily. Make it feel like rational reasoning.

**Length**: Approximately 1700-2100 words with a clear worked example (medical test or similar).
```
