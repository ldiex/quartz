Unlike traditional [[Gradient Descent|gradient descent]], which computes the gradient using the entire dataset, SGD computes the gradient using a randomly selected subset of the data, often just a single data point or a small "*mini-batch*."

## How SGD Works
1. **Initialization**: Start with randomly initialized model parameters.
2. **Data Shuffling**: Shuffle the dataset to ensure randomness in sample selection.
3. **Iteration**: For each training example (or mini-batch):
    - Compute the gradient of the loss function based on the selected data.
    - Update the model parameters in the direction that minimizes the loss, scaled by a learning rate.
4. **Convergence**: Repeat the process until the model converges or a predefined number of iterations is reached.