# Gradient Descent

> Here's the idea for gradient descent. What we're going to do is we're going to start off with some initial guesses for &theta;<sub>0</sub> and &theta;<sub>1</sub>. Doesn't really matter what they are, but a common choice would be we set &theta;<sub>0</sub> to 0, and set &theta;<sub>1</sub> to 0. What we're going to do in gradient descent is we'll keep changing &theta;<sub>0</sub> and &theta;<sub>1</sub> a little bit to try to reduce J(&theta;<sub>0</sub>, &theta;<sub>1</sub>), until hopefully, we wind at a minimum, or maybe at a local minimum.

So we have our hypothesis function and we have a way of measuring how well it fits into the data. Now we need to estimate the parameters in the hypothesis function. That's where gradient descent comes in.

Imagine that we graph our hypothesis function based on its fields &theta;<sub>0</sub> and &theta;<sub>1</sub> (actually we are graphing the cost function as a function of the parameter estimates). We are not graphing x and y itself, but the parameter range of our hypothesis function and the cost resulting from selecting a particular set of parameters.

![Cost Function of Linear Regression](https://raw.githubusercontent.com/rmolinamir/machine-learning-notes/main/docs/1-supervised-learning/2-gradient-descent/images/Cost-Function%20of%20Linear%20Regression.png)

We put &theta;<sub>0</sub> on the x axis and &theta;<sub>1</sub> on the y axis, with the cost function on the vertical z axis. The points on our graph will be the result of the cost function using our hypothesis with those specific &theta;<sub> </sub>parameters. We will know that we have succeeded when our cost function is at the very bottom of the pits in our graph, i.e. when its value is the minimum.

![Gradient Descent Graph](https://raw.githubusercontent.com/rmolinamir/machine-learning-notes/main/docs/1-supervised-learning/2-gradient-descent/images/Gradient-Descent%20Graph.png)

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Gradient Descent Algorithm](#gradient-descent-algorithm)
- [Gradient Descent Intuition](#gradient-descent-intuition)
- [Gradient Descent For Linear Regression](#gradient-descent-for-linear-regression)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Gradient Descent Algorithm

The way we do this is by taking the derivative (the tangential line to a function) of our cost function. The slope of the tangent is the derivative at that point and it will give us a direction to move towards. We make steps down the cost function in the direction with the steepest descent. The size of each step is determined by the parameter α, which is called the learning rate.

For example, the distance between each 'star' in the graph above represents a step determined by our parameter α. A smaller α would result in a smaller step and a larger α results in a larger step. The direction in which the step is taken is determined by the partial derivative of J(&theta;<sub>0</sub>,&theta;<sub>1</sub>). Depending on where one starts on the graph, one could end up at different points. The image above shows us two different starting points that end up in two different places.

The gradient descent algorithm is:

Repeat until convergence:

> &theta;<sub>j</sub> := &theta;<sub>j</sub> − α (∂ / ∂&theta;<sub>j</sub>) J(&theta;<sub>0</sub>,&theta;<sub>1</sub>)

Where:

`j = 0, 1`; represents the feature index number.

At each iteration j, one should simultaneously update the parameters &theta;<sub>1</sub>, &theta;<sub>2</sub>, ..., &theta;<sub>n</sub>. Updating a specific parameter prior to calculating another one on the j<sup>(th)</sup> iteration would yield to a wrong implementation.

![Gradient Descent Algorithm Iteration](https://raw.githubusercontent.com/rmolinamir/machine-learning-notes/main/docs/1-supervised-learning/2-gradient-descent/images/Gradient-Descent%20Algorithm%20Iteration.png)

## Gradient Descent Intuition

If the learning rate α is too small, gradient descent can be slow. If the learning rate α is too large, gradient descent can overshoot the minimum. It may fail to converge, or even diverge.

Gradient descent can converge to a local minimum, event with the learning rate α fixed. As we approach a local minimum, gradient descent will automatically take smaller steps. So, no need to decrease α over time.

![Gradient Descent Intuition 1.1](https://raw.githubusercontent.com/rmolinamir/machine-learning-notes/main/docs/1-supervised-learning/2-gradient-descent/images/Gradient-Descent%20Intuition%201.1.png)

![Gradient Descent Intuition 1.2](https://raw.githubusercontent.com/rmolinamir/machine-learning-notes/main/docs/1-supervised-learning/2-gradient-descent/images/Gradient-Descent%20Intuition%201.2.png)

![Gradient Descent Intuition 1.3](https://raw.githubusercontent.com/rmolinamir/machine-learning-notes/main/docs/1-supervised-learning/2-gradient-descent/images/Gradient-Descent%20Intuition%201.3.png)

On a side note, we should adjust our parameter α to ensure that the gradient descent algorithm converges in a reasonable time. Failure to converge or too much time to obtain the minimum value imply that our step size is wrong.

## Gradient Descent For Linear Regression

When specifically applied to the case of linear regression, a new form of the gradient descent equation can be derived. The point of all this is that if we start with a guess for our hypothesis and then repeatedly apply these gradient descent equations, our hypothesis will become more and more accurate.

So, this is simply gradient descent on the original cost function J. This method looks at every example in the entire training set on every step, and is called batch gradient descent. Note that, while gradient descent can be susceptible to local minima in general, the optimization problem we have posed here for linear regression has only one global, and no other local, optima; thus gradient descent always converges (assuming the learning rate α is not too large) to the global minimum. Indeed, J is a convex quadratic function. Here is an example of gradient descent as it is run to minimize a quadratic function.

![Gradient Descent For Linear Regression Example](https://raw.githubusercontent.com/rmolinamir/machine-learning-notes/main/docs/1-supervised-learning/2-gradient-descent/images/Gradient-Descent%20For%20Linear%20Regression%20Example.png)

The ellipses shown above are the contours of a quadratic function. Also shown is the trajectory taken by gradient descent, which was initialized at (48,30). The x’s in the figure (joined by straight lines) mark the successive values of θ that gradient descent went through as it converged to its minimum.
