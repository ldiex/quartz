Softmax is a mathematical function often used in machine learning, particularly in the context of classification problems where multiple classes are involved. It transforms a vector of real-valued scores (logits) into a probability distribution. This is useful because the outputs of models, especially neural networks, are often unbounded scores that need to be converted into probabilities that sum to $1$.

# Definition
Given a vector of scores $z = [z_1, z_2, \ldots, z_K]$, where $K$ is the number of classes, the softmax function is defined as:
$$
\text{softmax}(z_i) = \frac{e^{z_i}}{\sum_{j=1}^{K} e^{z_j}}
$$
for $i = 1, 2, \ldots, K$.
# Properties

1. **Probability Distribution**: The output of the softmax function is a probability distribution over the $K$ classes. Each output $\text{softmax}(z_i)$ lies in the range $(0, 1)$, and the sum of all outputs is equal to 1:   $$ \sum_{i=1}^{K} \text{softmax}(z_i) = 1 $$
2. **Exponentiation**: The use of the exponential function $e^{z_i}$ ensures that the outputs are positive. The exponentiation also amplifies the differences between scores: if one score is significantly larger than the others, its corresponding softmax probability will be higher.

3. **Sensitivity to Input**: The softmax function is sensitive to the input values. A small change in the input can lead to a large change in the output probabilities, particularly when the input scores are very close together.