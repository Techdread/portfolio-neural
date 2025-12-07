# H4: Knowledge Distillation — Three.js Visualization Prompt

## Visualization ID
H4

## Title
Knowledge Distillation

## Description
Teacher → student knowledge transfer visualised.

---

```
You are building an interactive Three.js visualization for a developer portfolio teaching AI/ML mathematics.

**Visualization ID**: H4
**Title**: Knowledge Distillation
**Description**: Teacher → student knowledge transfer visualised.

**Target Audience**: Software developers with limited math background learning ML concepts.

**Technical Requirements**:
- Language: TypeScript
- Framework: Three.js (latest stable)
- Quality: Polished, production-ready
- Performance: 60fps target

**Prerequisites for this visualization**:
- User understands neural networks and softmax

**Learning Objectives the visualization must support**:
1. See teacher and student as separate networks
2. Watch soft labels transfer from teacher to student
3. Understand temperature effect on softmax
4. See student gradually match teacher

**Required Interactive Features**:

**Network Display**:
1. **Teacher Network**: Large network visualization (many layers/neurons)
2. **Student Network**: Small network visualization (fewer layers/neurons)
3. **Size Comparison**: Visual scale difference
4. **Labels**: Clear "Teacher" and "Student" labels

**Input Flow**:
1. **Sample Input**: Image or data point
2. **Input to Both**: Same input goes to teacher and student
3. **Flow Animation**: Data flowing through networks

**Soft Label Visualization**:
1. **Teacher Output**: Probability distribution (bar chart)
2. **Student Output**: Probability distribution (bar chart)
3. **Side-by-Side Comparison**: Show distributions together
4. **Match Indicator**: How close student is to teacher

**Temperature Control**:
1. **Temperature Slider**: τ from 1 to 20
2. **Effect on Teacher Output**: Watch distribution soften
3. **Effect on Student Target**: Same temperature applied
4. **Comparison**: τ=1 vs higher τ outputs

**Distillation Training**:
1. **Train Button**: Start student training
2. **Epoch Counter**: Training progress
3. **Soft Loss Display**: KL divergence from teacher
4. **Hard Loss Display**: Cross-entropy from true labels
5. **Total Loss**: Weighted combination

**Training Animation**:
1. **Knowledge Flow**: Visual "knowledge" flowing from teacher to student
2. **Student Weights Updating**: Indicate learning
3. **Output Matching**: Watch student distribution approach teacher
4. **Progress Bar**: Overall training completion

**Before/After Comparison**:
1. **Untrained Student**: Random outputs
2. **Trained Student**: Matches teacher
3. **Test Samples**: Multiple samples to verify

**Accuracy Panel**:
1. **Teacher Accuracy**: Reference performance
2. **Student Accuracy**: After distillation
3. **Student Size**: Parameter count comparison
4. **Speed Comparison**: Inference time ratio

**Visual Design Requirements**:
- Clear size difference between networks
- Animated knowledge transfer effect
- Smooth distribution bar charts
- Temperature effect clearly visible
- Professional teacher/student metaphor

**Code Architecture Requirements**:
- Teacher model (pretrained or simulated)
- Student model (trainable)
- Soft label generation with temperature
- Distillation loss computation
- Training loop visualization

**Deliverables**:
Complete TypeScript implementation with network comparison, soft label visualization, temperature controls, and training animation.
```
