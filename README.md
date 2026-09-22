# Backprop

A neural network written from scratch, training live in the browser. No
TensorFlow, no autograd, no GPU. Every gradient comes from the chain rule
applied by hand.

Live: https://bxzex.github.io/backprop/

## What it implements

- **Forward pass** — a chain of `z = Wx + b` and a nonlinearity, with a sigmoid
  head producing one logit.
- **Backward pass** — the same chain in reverse. The derivative of cross entropy
  through a sigmoid collapses to `p - t`, which is where the recursion starts;
  each layer then multiplies by its local derivative and accumulates `dW` and
  `db`.
- **Optimiser** — minibatch gradient descent with momentum at 0.9, plus optional
  L2 regularisation applied to the weights but not the biases.
- **Initialisation** — He scaling for ReLU, Xavier otherwise. This is why a
  fresh network converges instead of stalling, and switching the activation
  rescales the initial weights to match.
- **Datasets** — two spirals, concentric rings, exclusive or, and two moons,
  each with adjustable Gaussian noise.

The decision boundary is drawn by evaluating the network across a grid and
shading every point by its output, so you are looking at the function the
network currently represents rather than an animation of one. The weight strip
shows the first layer, one column per hidden unit, signed and normalised.

Switching the activation to sigmoid is worth doing once: it converges visibly
slower than tanh on the same problem, which is the vanishing gradient in the
only form that ever made sense to me.

## Notes

One HTML file. No libraries. No build step.

Built by [bxzex](https://bxzex.com).
