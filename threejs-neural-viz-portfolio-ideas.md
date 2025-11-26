# Three.js Neural Network & Math Visualisation Portfolio

A learning-focused portfolio showcasing interactive visualisations of neural network concepts and their mathematical foundations using Three.js.

---

## Project Context

- **Tech Stack**: Three.js, JavaScript/TypeScript, TensorFlow.js (where applicable)
- **Purpose**: Educational portfolio demonstrating ML/AI concepts visually
- **Completed**: MNIST digit classifier visualisation

---

## Visualisation Ideas

### Category A: Linear Algebra Fundamentals

| ID | Title | Description |
|----|-------|-------------|
| A1 | Vector Operations | Visualise addition, subtraction, scaling, dot products in 2D/3D. Show dot product as similarity/angle. |
| A2 | Matrix Multiplication | Animate row-by-column multiplication step-by-step. Show matrices transforming space (rotation, scaling, shearing). |
| A3 | Matrix Transformations Gallery | Compose transformation matrices interactively. Demonstrate multiplication order effects. |
| A4 | Tensor Visualiser | Show scalars → vectors → matrices → 3D+ tensors. Demonstrate reshaping, broadcasting, slicing. |
| A5 | Eigenvalues & Eigenvectors | Vectors that only scale under transformation. Link to PCA for dimensionality reduction. |
| A6 | Basis Vectors & Change of Basis | Same point in different coordinate systems. Foundation for embedding spaces. |

### Category B: Calculus Essentials

| ID | Title | Description |
|----|-------|-------------|
| B1 | Derivative as Slope | Interactive function with draggable point showing tangent line. Visualise limit definition. |
| B2 | Partial Derivatives | 3D surface with slices showing change along each axis independently. |
| B3 | The Gradient Vector | Arrow pointing uphill on 2D surface in 3D view. Show why negative gradient = steepest descent. |
| B4 | Chain Rule Visualiser | Nested functions as pipeline. Animate derivatives multiplying through — the heart of backprop. |
| B5 | Product Rule | Area of rectangle: d(uv) = u·dv + v·du. Animate both terms contributing. |
| B6 | Sum Rule & Linearity | Derivatives distributing over addition. Simple but foundational. |

### Category C: Neural Network Operations

| ID | Title | Description |
|----|-------|-------------|
| C1 | Forward Pass Step-by-Step | Data flowing through layers: input → weighted sum → activation → output. Show actual numbers. |
| C2 | Backpropagation Walkthrough | Error gradients flowing backwards. Chain rule at each node, accumulating gradients. |
| C3 | Computational Graph | Expression trees for functions. Autodiff traversing forwards and backwards. |
| C4 | Activation Functions Gallery | Side-by-side: sigmoid, tanh, ReLU, Leaky ReLU, GELU. Show function AND derivative. |
| C5 | Loss Function Landscapes | Compare MSE, cross-entropy, hinge loss surfaces and optimisation behaviour. |
| C6 | Softmax & Cross-Entropy | Logits → probabilities → loss. Show harsh penalty for confident wrong predictions. |

### Category D: Optimisation Concepts

| ID | Title | Description |
|----|-------|-------------|
| D1 | Gradient Descent Variants | Compare vanilla, momentum, RMSprop, Adam on same surface. Show momentum escaping local minima. |
| D2 | Learning Rate Effects | Interactive slider: too small, just right, too large (divergence). Real-time path. |
| D3 | Batch vs Stochastic vs Mini-batch | Gradient estimate noise/accuracy differences affecting descent path. |
| D4 | Regularisation Visualised | L1 diamond vs L2 circle constraints. Why L1 promotes sparsity. |

### Category E: Architecture Visualisations

| ID | Title | Description |
|----|-------|-------------|
| E1 | CNN Layer Explorer | Filters sliding across images, feature maps at each layer, upload custom images. |
| E2 | Transformer Attention Visualiser | Attention heads as connection strengths between tokens. |
| E3 | Autoencoder Latent Space Navigator | Fly through VAE latent space, watch reconstructions morph. |
| E4 | RNN/LSTM Unrolled | Show temporal unrolling, hidden state persistence, gate operations. |

### Category F: Training Dynamics

| ID | Title | Description |
|----|-------|-------------|
| F1 | Loss Landscape Terrain | Loss surface as 3D terrain, gradient descent as ball rolling downhill. |
| F2 | Backprop Gradient Flow | Gradients flowing backwards, colour-coded by magnitude. Show vanishing/exploding. |
| F3 | Weight Initialisation Comparison | Xavier, He, random — activation distributions through layers over epochs. |
| F4 | Overfitting Visualised | Training vs validation loss diverging. Decision boundary becoming too complex. |

### Category G: Interactive Playgrounds

| ID | Title | Description |
|----|-------|-------------|
| G1 | Perceptron Playground | Drag points, watch perceptron find separating hyperplane. Show linear limits. |
| G2 | Embedding Space Explorer | word2vec/image embeddings in 3D with t-SNE/UMAP. Search and explore relationships. |
| G3 | GAN Training Dance | Generator vs discriminator loss tug-of-war, generated outputs evolving. |
| G4 | Decision Boundary Evolution | Watch classifier boundaries form during training on 2D data. |

### Category H: Advanced Concepts

| ID | Title | Description |
|----|-------|-------------|
| H1 | Neural Style Transfer Live | Optimisation process as content and style blend in real-time. |
| H2 | Spiking Neural Network | Temporal spike propagation dynamics. Neuromorphic computing intro. |
| H3 | Ensemble Voting Visualiser | Multiple models making predictions with visual votes combining. |
| H4 | Knowledge Distillation | Teacher → student knowledge transfer visualised. |

### Category I: Probability & Statistics

| ID | Title | Description |
|----|-------|-------------|
| I1 | Probability Distributions | Interactive normal, uniform, binomial. Parameter sliders shift shape. |
| I2 | Bayes' Theorem | Visual area diagrams: prior → evidence → posterior. |
| I3 | Maximum Likelihood | Find parameters making observed data most probable. |
| I4 | Information Theory Basics | Entropy, KL divergence visualised with distributions. |

---

## Reusable Prompt Template

Copy and customise the prompt below when requesting implementation help:

```
I'm building a Three.js visualisation portfolio for neural network and math concepts.

**Project ID**: [e.g., B4]
**Title**: [e.g., Chain Rule Visualiser]
**Description**: [copy from table above]

**Request**: [choose one or more]
- Architecture/component structure
- Core Three.js implementation
- Mathematical logic breakdown
- UI/interaction design
- Full implementation

**Preferences**:
- Style: [vanilla JS / TypeScript / React wrapper]
- Complexity: [minimal viable / polished / production-ready]
- Additional: [any specific requirements]
```

### Example Prompt

```
I'm building a Three.js visualisation portfolio for neural network and math concepts.

**Project ID**: B4
**Title**: Chain Rule Visualiser
**Description**: Nested functions as pipeline. Animate derivatives multiplying through — the heart of backprop.

**Request**: Full implementation

**Preferences**:
- Style: TypeScript
- Complexity: polished
- Additional: Include step-by-step animation controls
```

---

## Suggested Build Order

**Foundation Phase** (understand the math):
1. A1 → A2 → A4 (vectors, matrices, tensors)
2. B1 → B2 → B3 (derivatives, partials, gradients)
3. B4 → B5 (chain rule, product rule)

**Core Neural Net Phase**:
4. C4 (activation functions)
5. C1 → C2 (forward pass, backprop)
6. C5 → C6 (loss functions)

**Optimisation Phase**:
7. D2 → D1 (learning rate, then optimisers)
8. F1 (loss landscapes)

**Architecture Phase**:
9. E1 (CNNs) — builds on your MNIST work
10. E2 (transformers) — high interest topic

**Polish Phase**:
11. Pick favourites from G, H categories
12. Add probability concepts from I as needed

---

## Notes

- Each visualisation should have clear explanatory text alongside
- Consider adding "why this matters for ML" context to each
- Mobile responsiveness is a bonus but desktop-first is fine
- Performance: aim for 60fps, use instancing for many objects
