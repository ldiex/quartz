*Gradient ascent* is an optimization algorithm used to maximize a function, contrasting with [[Gradient Descent|gradient descent]], which is used for minimization.

# In CNNs to generate images
Gradient ascent is utilized in [[Convolutional Neural Networks (CNNs)|Convolutional Neural Networks (CNNs)]] to generate images that **maximally activate specific neurons or features within the network**. This technique is particularly useful for visualizing what a CNN has learned and understanding its internal representations.

The main idea for this is to fix the trained weights of the CNN and try to update the input image pixels in order to maximally activate a specific neuron.
$$
I^* = \underset{I}{\mathrm{argmax}} \left[ f(I) + R(I) \right] 
$$
where $f(I)$ stands for the neuron value, and $R(I)$ stands for the *natural image regularizer*. 

## Regularization
To ensure the generated images remain visually coherent and natural, regularization techniques are often applied. These can include penalizing the L2 norm of the image or applying Gaussian blur to reduce noise and artifacts during the optimization process.




