# Idea
The *cross entropy loss* is often used in classifier models in machine learning, where the model are supposed to obtain a probability distribution among the suspected categories which the input image may belong to. 

For a input image $x_i$, we have the predicted class distribution obtained by a model with parameters $\theta$, $P(y\mid x_i; \theta)$; and the true class distribution, $P^{\ast} (y\mid x_i)$. The loss function should indicate the similarity between these two distributions, and a natural way to do this is by [[Kullback–Leibler Divergence|KL divergence]]:
$$
\begin{aligned}
D_{\mathrm{KL}} (P^* \parallel P) &= \sum_{y} P^*(y\mid x_i) \log \dfrac{P^*(y\mid x_i)}{P(y \mid x_i;\theta)} \\
&= \sum_y P^*(y \mid x_i) \log P^* (y \mid x_i) - \sum_y  P^*(y \mid x_i) \log P(y \mid x_i ; \theta)
\end{aligned}
$$
Note that the first term is constant, so we just have
$$
\underset{\theta}{\mathrm{argmin}} \ D_{\mathrm{KL}}(P^* \parallel P) = \underset{\theta}{\mathrm{argmin}} \left[ -\sum_y P^*(y \mid x_i) \log P(y \mid x_i;\theta)\right] 
$$
and we could define the cross entropy loss as 
$$
H(P^*, P) =  -\sum_y P^*(y \mid x_i) \log P(y \mid x_i;\theta)
$$
In conclusion, the cross entropy loss is the natural loss based on KL divergence.

# Form with Softmax
If we define $y_i$ as the true distribution $P^*(y \mid x_i)$, and $\hat{y}_i$ as the predicted distribution generalized by [[Softmax|softmax]] activation function $\mathrm{softmax}(o_i)$, then the cross entropy loss is 
$$
\begin{aligned}
H(y \mid \hat{y}) &= - \sum_{i} y_i \log \hat{y}_i \\
& = - \sum_i y_i  \log \left[ \dfrac{\exp(o_i)}{\sum_j \exp(o_j)} \right] \\
&= \sum_i y_i \log \left[ \sum_j \exp (o_j)\right]  - \sum_i y_i o_i
\end{aligned}
$$
And the derivative of $H(y \mid \hat{y})$ with respect to any logit $o_i$ would be
$$
\partial_{o_i}  H(y \mid \hat{y}) = \dfrac{\exp(o_i)}{\sum_j \exp(o_j)} - y_i = \mathrm{softmax}(o_i) -y_i
$$

