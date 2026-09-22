# Backprop

A small neural network trained live in the browser. There's no TensorFlow and no autograd, just the chain rule written out by hand.

https://bxzex.github.io/backprop/

Pick a dataset (spirals, rings, XOR or moons) and watch the decision boundary form. The shading is the network's actual output sampled over a grid, so what you see is the function it has learned so far.

It uses SGD with momentum, optional L2, and He or Xavier initialisation depending on the activation. Try switching to sigmoid once. It trains noticeably slower than tanh on the same problem, and that's the vanishing gradient problem happening in front of you.
