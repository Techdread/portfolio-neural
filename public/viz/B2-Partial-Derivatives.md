# Partial Derivatives

*Derivatives of Multivariable Functions*

## 1. From One Variable to Many

In the last section, we mastered the derivative of functions like f(x) = x²—functions with a single input and a single output. But real-world problems rarely involve just one variable. The temperature in a room depends on position *and* time. The price of a house depends on square footage *and* location *and* age. And critically for us, the loss of a neural network depends on *millions* of weights simultaneously.

We need to extend our notion of derivative to handle functions with multiple inputs. The journey goes like this:

**Single variable**: f(x) = x² — One input, one output. We know how to differentiate this.

**Two variables**: f(x, y) = x² + y² — Two inputs, one output. This is where we're headed now.

**Many variables**: f(x₁, x₂, ..., xₙ) — n inputs, one output. This is what neural networks actually use.

The good news: once you understand the two-variable case, the extension to many variables is straightforward. The core insight stays exactly the same.

## 2. Visualizing f(x, y) as a Surface

When you have a function of one variable, you can draw it as a curve on a 2D graph—x on the horizontal axis, f(x) on the vertical. But what happens when you have two inputs?

With f(x, y), you need three dimensions: x and y spread out horizontally (forming a floor or "plane"), and the output f(x, y) rises vertically above each point. The result is a **surface**—a landscape of hills and valleys floating above the xy-plane.

Imagine a bedsheet draped over some objects. Each point on the floor has coordinates (x, y), and the height of the sheet at that point is f(x, y). Some spots are high (hilltops), some are low (valleys), and some are saddle-shaped (rising in one direction while falling in another).

In your visualization, you'll see this directly: a 3D surface that you can rotate and examine from different angles. Every point on that surface represents one combination of inputs (x, y) and its corresponding output f(x, y).

## 3. The Problem: Infinitely Many Directions

Here's where things get interesting. On a curve, there's only one direction to move—forward or backward along the line. The derivative tells you the slope in that single direction.

But on a surface, you can move in *infinitely many* directions from any point. You could walk due east (increasing x). You could walk due north (increasing y). You could walk northeast, or 37 degrees off north, or any angle you like. Each direction has its own slope—some paths climb steeply, others descend gently, and there might be one direction where the surface is perfectly flat.

How do we define "the derivative" when there's no single direction? The answer is: we don't try to capture everything at once. Instead, we break the problem into manageable pieces.

## 4. The Solution: One Direction at a Time

The key insight of partial derivatives is beautiful in its simplicity: **measure the slope in one coordinate direction at a time, pretending the other variables don't exist.**

Want to know how the function changes as x increases? Hold y fixed at some constant value, and measure the slope in the x-direction. That's the partial derivative with respect to x.

Want to know how it changes as y increases? Hold x fixed, and measure the slope in the y-direction. That's the partial derivative with respect to y.

By examining each direction independently, we can fully characterize how the surface behaves—at least in the axis directions. It's like asking "how steep is this hill going east?" and "how steep is it going north?" separately, rather than trying to describe every possible direction at once.

## 5. Partial Derivative Definition

Let's make this precise. For a function f(x, y):

**Partial derivative with respect to x**, written ∂f/∂x:
> "How does f change as x changes, while y is held constant?"

Mathematically, it's the same limit definition as before, but only x moves:

**∂f/∂x = lim(h→0) [f(x + h, y) - f(x, y)] / h**

Notice that y appears in both terms with the same value—it doesn't change. We're taking a regular derivative, but treating y as if it were just a number like 2 or 7.

**Partial derivative with respect to y**, written ∂f/∂y:
> "How does f change as y changes, while x is held constant?"

**∂f/∂y = lim(h→0) [f(x, y + h) - f(x, y)] / h**

Now x stays fixed while y varies.

Each partial derivative answers a specific question: if I adjust *this one input* while freezing everything else, how does the output respond?

## 6. The Slice Interpretation

Here's where the visualization becomes powerful. When you hold y constant at some value c, you're essentially slicing through the 3D surface with a vertical plane parallel to the xz-axes.

That slice reveals a curve—a 2D cross-section of the surface. This curve shows how f changes with x (when y = c), and **∂f/∂x is simply the slope of that curve**. It's the same derivative concept from B1, just applied to a slice of a higher-dimensional object.

Similarly, if you hold x constant and vary y, you get a different slice—a curve in the yz-plane. The slope of *that* curve is ∂f/∂y.

In your interactive visualization, try this:

1. Look at the surface from the side, along the y-axis. You'll see the profile of an x-slice—a curve whose slope is ∂f/∂x.
2. Now rotate to look along the x-axis. The profile you see is a y-slice, with slope ∂f/∂y.
3. Drag the slice plane back and forth. Watch how the curve's shape (and therefore its slope) changes at different slice positions.

This slice-and-slope interpretation is the most important intuition for partial derivatives. Whenever you're confused about what ∂f/∂x means, think: "slice the surface parallel to the xz-plane, and find the slope of the resulting curve."

## 7. Notation

You'll encounter several notations for partial derivatives:

**∂f/∂x** — The standard notation. The curly "∂" (sometimes called "del" or "partial") signals that this is a partial derivative, not an ordinary one. Read it as "the partial derivative of f with respect to x" or simply "partial f partial x."

**∂/∂x [f]** — Operator notation. The ∂/∂x is an operator that acts on functions, telling you "differentiate with respect to x."

**fₓ** or **f_x** — Subscript notation. Compact and common in physics and engineering. The subscript indicates which variable you're differentiating with respect to.

**∂z/∂x** — When z = f(x, y), this is equivalent to ∂f/∂x. It emphasizes that z (the height) changes as x changes.

Why the curly ∂ instead of the straight d? It's a visual reminder that other variables exist and are being held constant. When you see d, there's typically only one variable. When you see ∂, there are multiple variables, and you're focusing on just one.

## 8. Computing Partial Derivatives

The mechanical process is surprisingly easy: **treat all other variables as constants, then differentiate normally.**

Let's work through an example. Suppose f(x, y) = x²y + 3xy² - 5y.

**To find ∂f/∂x:** Pretend y is just a constant (like the number 7). Then:
- x²y differentiates to 2xy (the y is just a coefficient)
- 3xy² differentiates to 3y² (again, y² is just a coefficient)
- -5y differentiates to 0 (it's a "constant" since there's no x)

So **∂f/∂x = 2xy + 3y²**

**To find ∂f/∂y:** Now pretend x is the constant:
- x²y differentiates to x² (x² is the coefficient of y)
- 3xy² differentiates to 6xy (power rule on y²)
- -5y differentiates to -5

So **∂f/∂y = x² + 6xy - 5**

Notice that both partial derivatives are themselves functions of x and y. The slope in the x-direction depends on where you are on the surface—both your x-coordinate and your y-coordinate affect it.

## 9. Why This Matters for Machine Learning

Now for the payoff. A neural network's loss function isn't f(x, y)—it's f(w₁, w₂, w₃, ..., wₙ) where n might be millions or billions. Each wᵢ is a weight in the network.

When training, we need to answer this question for every single weight: **"If I nudge this one weight slightly, how does the overall loss change?"** That's exactly what a partial derivative tells us.

∂L/∂w₁ says: "Holding all other weights fixed, how does the loss L respond to changes in w₁?"

∂L/∂w₂ says: "Holding all other weights fixed, how does L respond to changes in w₂?"

And so on, for every weight in the network.

Why do we need this? Because gradient descent updates each weight independently:

**w₁_new = w₁_old - learning_rate × ∂L/∂w₁**

**w₂_new = w₂_old - learning_rate × ∂L/∂w₂**

Each weight gets its own update based on its own partial derivative. If ∂L/∂w₁ is large and positive, that weight is contributing significantly to the loss—we should decrease it. If ∂L/∂w₁ is small, that weight doesn't matter much to the current prediction error.

The algorithm called **backpropagation** computes all these partial derivatives efficiently. Rather than calculating each ∂L/∂wᵢ from scratch (which would be impossibly slow), backpropagation reuses intermediate calculations by working backward through the network. But regardless of *how* they're computed, the *meaning* is the same: each partial derivative measures the sensitivity of the loss to one specific weight.

## 10. The Gradient Preview

We've seen that a function of n variables has n partial derivatives—one for each input. It's natural to collect them all into a single object: the **gradient**.

For f(x, y), the gradient is the vector:

**∇f = (∂f/∂x, ∂f/∂y)**

For a neural network loss L(w₁, w₂, ..., wₙ), the gradient is:

**∇L = (∂L/∂w₁, ∂L/∂w₂, ..., ∂L/∂wₙ)**

This vector has a remarkable property: **it points in the direction of steepest ascent**. If you want to climb the surface as quickly as possible, follow the gradient. If you want to descend as quickly as possible (which is exactly what gradient descent does), go in the *opposite* direction.

We'll explore the gradient in depth in the next section. For now, just remember: partial derivatives are the components of the gradient. Each partial tells you the slope in one coordinate direction; the gradient assembles them into a vector that captures the full picture of how the function changes.

## Wrapping Up

Partial derivatives extend the concept of "rate of change" to functions with multiple inputs. The key insight is simple: **measure change in one direction at a time, holding everything else constant.**

When you look at your 3D visualization, remember that each slice through the surface gives you an ordinary curve, and the partial derivative is the slope of that curve. The x-slices reveal ∂f/∂x; the y-slices reveal ∂f/∂y.

For machine learning, partial derivatives answer the essential training question: "How does each individual weight affect the loss?" By computing these sensitivities for every parameter, backpropagation enables neural networks to learn—adjusting millions of weights simultaneously, each in its own direction toward lower loss.

In the next section, we'll see how these individual partial derivatives combine into the gradient vector—and why that vector always points uphill.
