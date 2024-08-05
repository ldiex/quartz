In neural networks, *Xavier initialization* helps maintain consistent variance of activations and gradients throughout the network layers. This prevents the [[Stable Activations and Gradients in Deep Learning#Vanishing Gradients|vanishing gradients]] and [[[Stable Activations and Gradients in Deep Learning#Exploding Gradients|exploding gradient]] as they propagate through the network during training

Consider the scale distribution of an output $o_i$ for some fully connected layer without nonlinearities. With $n_{\mathrm{in}}$ inputs $x_j$ and their associated weights $w_{ij}$ for this layer, an output is given by 
$$
o_i = \sum_{j= 1}^{n_\mathrm{{in}}} w_{ij} x_j
$$
The weights $w_{ij}$ are all drawn independently from the same distribution. Assume the distribution has zero mean and variance $\sigma^{2}$, and the inputs to the layer $x_j$ also have zero man and variance $\gamma^{2}$ and that they are independent of $w_{ij}$ and independent of each other. In this case, we can compute the mean of $o_i$
$$
\mathrm{E}[o_i] = \sum_{j = 1}^{n_\mathrm{in}} \mathrm{E}[w_{ij} x_j] = \sum_{j = 1}^{n_\mathrm{in}} \mathrm{E}[w_{ij}]\mathrm{E}[x_j] = 0
$$
and the variance:
$$
\mathrm{Var}[o_i] = \mathrm{E}[o_i^{2}] - \mathrm{E}^2[o_i] = \sum_{j = 1}^{n_\mathrm{in}} \mathrm{E}[w_{ij}^{2}] \mathrm{E}[x_j^{2}] - 0 = n_\mathrm{in} \sigma^{2}\gamma^{2}
$$
One way to keep the variance fixed is to set $n_\mathrm{in}σ^{2}=1$. Now consider backpropagation. There we face a similar problem, albeit with gradients being propagated from the layers closer to the output. Using the same reasoning as for forward propagation, we see that the gradients’ variance can blow up unless $n_\mathrm{out}\sigma^{2} = 1$, where $n_\mathrm{out}$ is the number of outputs of this layer. This leaves us in a dilemma: we cannot possibly satisfy both conditions simultaneously. Instead, we simply try to satisfy:
$$
\dfrac{1}{2} (n_\mathrm{in} + n_\mathrm{out}) \sigma^{2} = 1 \iff \sigma = \sqrt{ \dfrac{2}{n_\mathrm{in}+ n_\mathrm{out}} } 
$$
This is the reasoning underlying the now-standard and practically beneficial *Xavier initialization*

 We can also adapt this to choose the variance when sampling weights from a uniform distribution. Note that the uniform distribution $U(−a,a)$ has variance $\dfrac{a^{2}}{3}$. Plugging $\dfrac{a^{2}}{3}$ into our condition on $\sigma^{2}$ prompts us to initialize according to
$$
U\left( -\sqrt{ \dfrac{6}{n_\mathrm{in} + n_\mathrm{out}} }, \sqrt{ \dfrac{6}{n_\mathrm{in}+ n_\mathrm{out}} } \right) 
$$
