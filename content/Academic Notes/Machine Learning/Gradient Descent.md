# Idea
*Gradient descent* is an optimization algorithm used to minimize a function by iteratively moving towards the steepest descent, which is indicated by the negative [[Differential of Multivariable Functions#梯度|gradient]]. It is widely used in [[Machine Learning|machine learning]] and [[Deep Learning|deep learning]] to minimize the [[Loss Functions|cost function]], thereby improving model accuracy.

# How It Works
1. **Initialize Parameters**: Start with random values for the model parameters (weights).
2. **Compute Gradient**: Calculate the gradient (partial derivatives) of the cost function with respect to the parameters. This tells you the direction of the steepest ascent.
3. **Update Parameters**: Adjust the parameters in the opposite direction of the gradient to minimize the cost function:
$$
\theta = \theta - \alpha \nabla J(\theta)
$$
   where $\theta$ is the parameters, $\alpha$ is the *learning rate* and $\nabla J(\theta)$ is the gradient of the cost function.
4. **Iterate**: Repeat the process until convergence (i.e., when changes in the cost function are negligible).

#
