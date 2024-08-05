# Issues
## Vanishing Gradients
The *vanishing gradient* problem occurs when the gradients of the [[Loss Functions|loss function]] with respect to the network's weights become exceedingly small as they are propagated back through the layers. This typically happens in networks with many layers, where the gradients are calculated using the chain rule, resulting in the multiplication of many small numbers. Consequently, the gradients shrink exponentially as they move backward through the network, leading to negligible updates in the initial layers' weights. This can significantly slow down the training process or even halt it altogether, preventing the network from learning effectively.
## Exploding Gradients
The *exploding gradient* problem is the opposite of the vanishing gradient problem. It occurs when the gradients become excessively large during backpropagation, leading to large updates in the network's weights. This can cause the model parameters to oscillate wildly or diverge, making it difficult for the model to converge to an optimal solution.

# Tools
## Activation Function
use [[Rectified Linear Unit (ReLU)]]

## Weight Initialization
use [[Xavier Initialization]] or [[He Initialization]]

## Input Normalization
use [[Batch Normalization]]