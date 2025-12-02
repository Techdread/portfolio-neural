# Tensors: From Scalars to N-Dimensional Arrays

You've mastered vectors (1D) and matrices (2D). Now it's time to remove the training wheels and meet the general concept that encompasses them both: the **tensor**. In deep learning, everything is a tensor. Your input data, your weights, your gradients, your outputs. Understanding tensors means understanding the fundamental data structure of modern AI.

The good news: if you understand arrays in programming, you already understand tensors. They're just arrays that can have any number of dimensions.


## 1. What is a Tensor?

A tensor is a container for numbers arranged in a regular grid of any dimensionality. That's it. The term comes from physics and differential geometry where it has a more specific meaning, but in machine learning, "tensor" simply means "n-dimensional array."

```typescript
// These are all tensors:
const scalar = 42;                          // 0D tensor
const vector = [1, 2, 3];                   // 1D tensor
const matrix = [[1, 2], [3, 4]];            // 2D tensor
const cube = [[[1, 2], [3, 4]], [[5, 6], [7, 8]]];  // 3D tensor
```

The key insight is that vectors and matrices aren't special cases with their own rules. They're just tensors with 1 and 2 dimensions respectively. Once you understand tensors, you understand all of them simultaneously.


## 2. The Tensor Hierarchy

Let's climb the ladder from the simplest to the most complex, with real ML examples at each level.

**Rank 0: Scalar (single number)**

A scalar is a tensor with zero dimensions. It's just one number, but frameworks still treat it as a tensor for consistency.

```python
# NumPy
loss = np.array(0.342)
print(loss.shape)  # ()  — empty tuple means 0 dimensions

# TensorFlow.js
const loss = tf.scalar(0.342);
console.log(loss.shape);  // []
```

*ML examples:* Loss value, learning rate, accuracy metric, single prediction probability.


**Rank 1: Vector (1D array)**

A vector is a tensor with one dimension. We covered these in A1, but now you can see them as part of the bigger picture.

```python
# NumPy
bias = np.array([0.1, -0.2, 0.3, 0.0])
print(bias.shape)  # (4,)

# TensorFlow.js
const bias = tf.tensor1d([0.1, -0.2, 0.3, 0.0]);
console.log(bias.shape);  // [4]
```

*ML examples:* Bias vector in a layer, word embedding for a single word, 1D signal like audio amplitude over time, output probabilities for classification.


**Rank 2: Matrix (2D array)**

Matrices are tensors with two dimensions. You know these from A2 and A3.

```python
# NumPy
weights = np.array([
    [0.1, 0.2, 0.3],
    [0.4, 0.5, 0.6]
])
print(weights.shape)  # (2, 3) — 2 rows, 3 columns

# TensorFlow.js
const weights = tf.tensor2d([
    [0.1, 0.2, 0.3],
    [0.4, 0.5, 0.6]
]);
console.log(weights.shape);  // [2, 3]
```

*ML examples:* Weight matrix connecting layers, grayscale image, batch of 1D data points, attention scores, confusion matrix.


**Rank 3: 3D Tensor**

Here's where we go beyond familiar territory. A 3D tensor is like a stack of matrices, or a cube of numbers.

```python
# NumPy — RGB image: height × width × channels
image = np.zeros((224, 224, 3))  # 224×224 pixels, 3 color channels
print(image.shape)  # (224, 224, 3)

# TensorFlow.js — batch of vectors
batchOfVectors = tf.zeros([32, 128]);  # 32 samples, 128 features each
// Wait, that's 2D. Let's do a true 3D:
sequenceData = tf.zeros([32, 50, 256]);  # 32 sequences, 50 timesteps, 256 features
console.log(sequenceData.shape);  // [32, 50, 256]
```

*ML examples:* Single RGB/color image (H×W×C), batch of grayscale images (batch×H×W), sequence data for RNNs (batch×timesteps×features), word embeddings for a sentence (words×embedding_dim... often batched to 3D).


**Rank 4+: Higher-Dimensional Tensors**

For images in neural networks, we typically work with 4D tensors:

```python
# NumPy — batch of RGB images
batch_of_images = np.zeros((32, 224, 224, 3))
# 32 images, each 224×224 pixels, each pixel has 3 color values
print(batch_of_images.shape)  # (32, 224, 224, 3)

# TensorFlow.js
const imageBatch = tf.zeros([32, 224, 224, 3]);
console.log(imageBatch.shape);  // [32, 224, 224, 3]
```

*ML examples:* Batch of color images (batch×H×W×C), video data (batch×frames×H×W×C makes 5D), transformer attention (batch×heads×sequence×sequence).


## 3. Shape, Rank, and Size

Three numbers tell you everything about a tensor's structure:

**Shape** is a tuple listing the size of each dimension.

```python
tensor = np.zeros((2, 3, 4))
print(tensor.shape)  # (2, 3, 4)
```

Read this as: "2 blocks, each containing 3 rows, each row having 4 elements."

**Rank** (or "ndim" in NumPy) is the number of dimensions. It's simply the length of the shape tuple.

```python
print(tensor.ndim)  # 3
print(len(tensor.shape))  # 3 — same thing
```

**Size** is the total count of numbers in the tensor. Multiply all shape dimensions together.

```python
print(tensor.size)  # 2 × 3 × 4 = 24
```

```typescript
// TensorFlow.js
const tensor = tf.zeros([2, 3, 4]);
console.log(tensor.shape);      // [2, 3, 4]
console.log(tensor.shape.length); // 3 (rank)
console.log(tensor.size);       // 24
```

**Why this matters:** Neural network layers have strict expectations about input shapes. A Conv2D layer expects 4D input (batch, height, width, channels). A Dense layer expects 2D input (batch, features). Shape mismatches are the most common errors you'll encounter.


## 4. Reshaping: Same Data, Different Shape

Reshaping rearranges the structure of a tensor without changing its data. The total number of elements must stay the same.

```python
# Start with a 2×6 matrix (12 elements)
original = np.array([
    [1, 2, 3, 4, 5, 6],
    [7, 8, 9, 10, 11, 12]
])

# Reshape to 3×4 (still 12 elements)
reshaped = original.reshape(3, 4)
# [[1, 2, 3, 4],
#  [5, 6, 7, 8],
#  [9, 10, 11, 12]]

# Reshape to 12×1 (column vector)
column = original.reshape(12, 1)

# Reshape to 1D (flatten)
flat = original.reshape(-1)  # -1 means "figure out this dimension"
# [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
```

```typescript
// TensorFlow.js
const original = tf.tensor2d([[1, 2, 3, 4, 5, 6], [7, 8, 9, 10, 11, 12]]);
const reshaped = original.reshape([3, 4]);
const flat = original.flatten();  // or reshape([-1])
```

**Common reshapes in neural networks:**

*Flattening for dense layers:* After convolutional layers, you often need to flatten the 3D feature maps into a 1D vector for dense layers.

```python
# After conv layers: (batch, 7, 7, 512)
# Need to feed to Dense layer: (batch, features)
x = x.reshape(batch_size, -1)  # becomes (batch, 7*7*512) = (batch, 25088)
```

*Expanding dimensions:* Add a dimension of size 1 for broadcasting or to meet layer expectations.

```python
vector = np.array([1, 2, 3])  # shape (3,)
row = vector.reshape(1, 3)    # shape (1, 3) — row vector
col = vector.reshape(3, 1)    # shape (3, 1) — column vector
batched = vector.reshape(1, 3, 1)  # shape (1, 3, 1)

# Or use expand_dims
row = np.expand_dims(vector, axis=0)  # adds dimension at position 0
```

*Preparing images:* Single images need a batch dimension added before feeding to models.

```python
image = load_image()  # shape (224, 224, 3)
batched = image.reshape(1, 224, 224, 3)  # shape (1, 224, 224, 3)
# Or: batched = np.expand_dims(image, axis=0)
```


## 5. Broadcasting: Operations on Mismatched Shapes

Broadcasting is the magic that lets you add a scalar to a matrix, or multiply a matrix by a vector, without explicitly copying data. It's how frameworks handle operations between tensors of different shapes.

**The core idea:** When shapes don't match, smaller tensors are "virtually stretched" to match larger ones.

```python
# Add scalar to matrix (scalar broadcasts to every element)
matrix = np.array([[1, 2], [3, 4]])
result = matrix + 10
# [[11, 12],
#  [13, 14]]

# Add vector to matrix (vector broadcasts across rows)
vector = np.array([100, 200])
result = matrix + vector
# [[101, 202],
#  [103, 204]]
```

**Broadcasting rules (simplified):**

1. Compare shapes from right to left (trailing dimensions first)
2. Dimensions are compatible if they're equal, or if one of them is 1
3. Missing dimensions on the left are treated as size 1

```python
A: (4, 3)
B:    (3)  ← B is treated as (1, 3), then broadcast to (4, 3)
Result: (4, 3) ✓

A: (2, 3, 4)
B:       (4)  ← B is treated as (1, 1, 4), broadcast to (2, 3, 4)
Result: (2, 3, 4) ✓

A: (2, 3, 4)
B:    (3, 1)  ← broadcast to (2, 3, 4)
Result: (2, 3, 4) ✓

A: (2, 3)
B: (4, 3)  ← 2 ≠ 4 and neither is 1
Result: Error! ✗
```

**Common broadcasting patterns in ML:**

*Bias addition:* Add a bias vector to every sample in a batch.

```python
# batch of predictions: (32, 10)
# bias vector: (10,)
# bias broadcasts across the batch dimension
output = predictions + bias  # shape (32, 10)
```

*Normalization:* Subtract mean and divide by std across features.

```python
# data: (1000, 64) — 1000 samples, 64 features
mean = data.mean(axis=0)  # shape (64,)
std = data.std(axis=0)    # shape (64,)
normalized = (data - mean) / std  # broadcasts work automatically
```

*Attention masks:* Broadcast a mask across batch or head dimensions.

```python
# attention scores: (batch, heads, seq_len, seq_len)
# mask: (1, 1, seq_len, seq_len)
# mask broadcasts across batch and heads
masked = scores + mask  # where mask is 0 or -inf
```


## 6. Slicing and Indexing

Extracting parts of tensors is essential for inspecting data, selecting samples, and implementing attention mechanisms.

**Single element access:**

```python
tensor = np.array([
    [[1, 2], [3, 4]],
    [[5, 6], [7, 8]]
])  # shape (2, 2, 2)

# Access element at position [1, 0, 1]
element = tensor[1, 0, 1]  # 6

# In TensorFlow.js (more verbose)
const element = tensor.slice([1, 0, 1], [1, 1, 1]).dataSync()[0];
```

**Slice notation:** Use `start:stop` to grab ranges. Omit start or stop to mean "from beginning" or "to end."

```python
matrix = np.array([
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12]
])

# First two rows
matrix[:2]      # [[1,2,3,4], [5,6,7,8]]

# Last column
matrix[:, -1]   # [4, 8, 12]

# Top-left 2×2 block
matrix[:2, :2]  # [[1,2], [5,6]]

# Every other row
matrix[::2]     # [[1,2,3,4], [9,10,11,12]]
```

```typescript
// TensorFlow.js
const matrix = tf.tensor2d([[1,2,3,4], [5,6,7,8], [9,10,11,12]]);

// First two rows
matrix.slice([0, 0], [2, 4]);  // start at [0,0], take [2 rows, 4 cols]

// More ergonomic with gather for specific indices
const rows = matrix.gather([0, 2]);  // rows 0 and 2
```

**Advanced indexing:** Select specific elements using arrays of indices.

```python
# Select specific rows
indices = [0, 2]
selected = matrix[indices]  # rows 0 and 2

# Boolean masking
mask = matrix > 5
filtered = matrix[mask]  # [6, 7, 8, 9, 10, 11, 12]
```

**ML-relevant slicing examples:**

```python
# Get a single sample from a batch
batch = np.zeros((32, 224, 224, 3))
single_image = batch[0]  # shape (224, 224, 3)

# Get the red channel only
red_channel = batch[:, :, :, 0]  # shape (32, 224, 224)

# Get predictions for class 0 across batch
predictions = np.zeros((32, 10))  # 32 samples, 10 classes
class_0_probs = predictions[:, 0]  # shape (32,)

# Sequence slicing for transformers
sequence = np.zeros((32, 512, 768))  # batch, seq_len, hidden
first_token = sequence[:, 0, :]  # CLS token: shape (32, 768)
```


## 7. Why This Matters for ML/AI

**All neural network data is tensors.** There's no escaping them. Input images, text embeddings, weight matrices, gradients during backprop, attention scores. Everything flows through your network as tensors.

**Shape errors are the #1 debugging challenge.** You'll see errors like "Expected shape (None, 784) but got (32, 28, 28)" constantly. Understanding tensor shapes lets you trace through your network mentally and spot where dimensions go wrong.

```python
# Common debugging pattern
def debug_shapes(model, sample_input):
    x = sample_input
    print(f"Input: {x.shape}")
    for i, layer in enumerate(model.layers):
        x = layer(x)
        print(f"After layer {i} ({layer.name}): {x.shape}")
```

**Broadcasting prevents bugs (and causes them).** Broadcasting is powerful but can silently do the wrong thing if you're not careful. A shape (64, 1) tensor and a shape (1, 64) tensor will broadcast to (64, 64) when multiplied. Is that what you wanted? Understanding broadcasting helps you write correct code and catch bugs.

**Reshaping connects layer types.** Convolutional layers output 4D tensors. Dense layers expect 2D. Reshape (flatten) bridges them. Transformer attention reshapes constantly (splitting heads, merging heads). Know your reshapes.

**Efficient batching requires tensor thinking.** Processing one sample at a time is slow. Batching multiple samples into a single tensor lets the GPU parallelize. But this means every operation must handle the batch dimension correctly. Tensor operations naturally handle this through broadcasting and batched matrix multiplication.

```python
# Slow: loop over samples
for sample in samples:
    output = model(sample)

# Fast: batch everything
outputs = model(samples_tensor)  # GPU processes all at once
```


## Wrapping Up

Tensors are the universal language of deep learning. They generalize the vectors and matrices you already know to arbitrary dimensions, and the operations you've learned (multiplication, addition, transformation) extend naturally.

The key concepts to internalize: shape tells you structure, reshaping rearranges without changing data, broadcasting handles mismatched shapes automatically, and slicing extracts the pieces you need.

In your Three.js visualization, watch how data flows through tensor operations. See how a 4D batch of images gets reshaped, convolved, and flattened as it moves through a CNN. That visual intuition will make debugging shape errors almost trivial.

Next, we'll explore the eigenvalue decomposition, which reveals the fundamental "directions" that a matrix transformation prefers.
