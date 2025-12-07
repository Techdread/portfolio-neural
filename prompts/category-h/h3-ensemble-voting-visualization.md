# H3: Ensemble Voting Visualiser — Three.js Visualization Prompt

## Visualization ID
H3

## Title
Ensemble Voting Visualiser

## Description
Multiple models making predictions with visual votes combining.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: H3
**Title**: Ensemble Voting Visualiser
**Description**: Multiple models making predictions with visual votes combining.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands classification

**Learning Objectives the visualization must support**:
1. See individual model predictions
2. Watch votes aggregate into ensemble prediction
3. Compare voting schemes
4. Understand how diversity helps

**Required Interactive Features**:

**Model Panel**:
1. **Model Icons**: Visual representation of each model (3-7 models)
2. **Model Types**: Different shapes/colors for different model types
3. **Model Names**: Labels (Model 1, Model 2, or type names)
4. **Individual Predictions**: Each model shows its prediction

**Input Display**:
1. **Current Sample**: Show the input being classified
2. **Sample Selector**: Choose different test samples
3. **Feature Display**: Show input features visually
4. **True Label**: Ground truth (for comparison)

**Voting Visualization**:
1. **Vote Casting Animation**: Votes fly from models to ballot box
2. **Vote Counters**: Tally for each class
3. **Probability Bars**: For soft voting, show probability contributions
4. **Winner Highlight**: Final ensemble prediction

**Voting Scheme Toggle**:
1. **Hard Voting**: Each model casts one vote
2. **Soft Voting**: Models contribute probability distributions
3. **Weighted Voting**: Some models have more influence
4. **Scheme Comparison**: Side-by-side results

**Weight Controls** (for weighted voting):
1. **Weight Sliders**: Adjust each model's weight
2. **Auto-Weight**: Button to set weights by validation accuracy
3. **Weight Display**: Visual size of model's influence

**Agreement Analysis**:
1. **Agreement Meter**: How much models agree
2. **Disagreement Highlighting**: Show where models differ
3. **Confidence Indicator**: Ensemble certainty

**Accuracy Comparison**:
1. **Individual Accuracy**: Each model's performance
2. **Ensemble Accuracy**: Combined performance
3. **Improvement Indicator**: Show ensemble > individuals

**Decision Boundary View** (for 2D data):
1. **Individual Boundaries**: Each model's boundary
2. **Ensemble Boundary**: Combined decision boundary
3. **Overlay Mode**: See all boundaries together
4. **Voting Regions**: Where models agree/disagree

**Visual Design Requirements**:
- Distinct icons for each model
- Animated vote transfer
- Clear tally displays
- Color-coded by class prediction
- Professional ballot box metaphor

**Code Architecture Requirements**:
- Mock model predictions (or simple real models)
- Voting aggregation functions
- Animation sequencing for votes
- Multiple visualization modes
- Accuracy tracking

**Deliverables**:
Complete TypeScript implementation with model display, animated voting, scheme comparison, and accuracy analysis.
```
