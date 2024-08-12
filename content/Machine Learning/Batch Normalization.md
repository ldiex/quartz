*Batch normalization* is a technique that normalizes the inputs of each layer to have **zero mean** and **unit variance** during training. This helps in [[Stable Activations and Gradients in Deep Learning|stabilizing and accelerating the training process]] by reducing the internal covariate shift, which refers to the change in the distribution of network activations due to the updates of the parameters in the previous layers. Batch normalization allows the use of higher learning rates and makes the training less sensitive to the initial weights

Consider a batch of activations at some layer. To make each dimension *unit gaussian*(with zero mean and unit variance), we just need to apply:
$$
\hat{x}^{(k)} = \dfrac{x^{(k)}-\mathrm{E}[x^{(k)}]}{\sqrt{ \mathrm{Var}[x^{(k)}] }}
$$
Now we could come up with the batch normalization layer:
- **Input**: Values of $x$ over a mini-batch: $\mathcal B = \left\{ x_1, \ldots ,x_m \right\}$; Parameters to be learned: $\gamma, \beta$
- **Output**: $\left\{ y_i = \mathrm{BN}_{\gamma,\beta}(x_i) \right\}$
- **Algorithm**: 
$$
\begin{aligned}
& \mu_{\mathcal B}=   \dfrac{1}{m} \sum_{i = 1}^m x_i \\
& \sigma_{\mathcal B}^{2} = \dfrac{1}{m} \sum_{i = 1}^m\left( x_i - \mu_{\mathcal B} \right) ^{2} \\
&\hat{x}_i  = \dfrac{x_i - \mu_{\mathcal B}}{\sqrt{ \sigma_{\mathcal B}^{2} + \epsilon }} \\
&y_i = \gamma \hat{x}_i + \beta \equiv \mathrm{BN}_{\gamma,\beta} (x_i)
\end{aligned}
$$
Where the $\epsilon$ is a small constant to prevent division by zero when normalizing the input features.

This layer could
- Improve gradient flow through the network
- Allow higher learning rates
- Reduces the strong dependence on initialization
- Acts as a form of regularization in a funny way, and slightly reduces the need for dropout, maybe

