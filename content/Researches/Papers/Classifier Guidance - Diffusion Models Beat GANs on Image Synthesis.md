---
zotero-key: 8E7ST624
zt-attachments:
  - "657"
title: Diffusion Models Beat GANs on Image Synthesis
authors:
  - Prafulla Dhariwal
  - Alex Nichol
collections:
  - Generative Models > Computer Vision > Artificial Intelligence
publish-date: 2021
url: http://arxiv.org/abs/2105.05233
DOI: 10.48550/arXiv.2105.05233
---
# Direct Guidance
In [[Denoising Diffusion Probabilistic Models (DDPM)|DDPM]], we focus on modeling just the data distribution $p(\boldsymbol x)$. However, we are often also interested in learning conditional distribution $p(\boldsymbol x | y)$, which would enable us to explicitly control the data we generate through **conditional information** $y$. 

A natural way to add conditioning information is simply alongside the timestep information, at each iteration. Recall that from the joint distribution of $\boldsymbol x_1, \ldots ,\boldsymbol x_T$ can be derived from the product of [[Denoising Diffusion Probabilistic Models (DDPM)#Transition Distribution|transition distributions]]
$$
p(\boldsymbol x_{0:T}) = p(\boldsymbol x_T) \prod_{t = 1}^T p_{\boldsymbol \theta}(\boldsymbol x_{t - 1} | \boldsymbol x_t)
$$
We can simply add arbitrary conditioning information $y$ at each transition step as
$$
p(\boldsymbol x_{0:T}| y) = p(\boldsymbol x_T) \prod_{t = 1}^T p_{\boldsymbol \theta}(\boldsymbol x_{t - 1} | \boldsymbol x_t | y)
$$
where $y$ could be a text encoding in image-text generation, or a low-resolution image to perform super-resolution on. Now we can learn the core neural network of a DDPM as before.

However, a caveat of this vanilla formulation is that **a conditional diffusion model trained in this way may potentially learn to ignore or downplay any given conditioning information**. Guidance is therefore proposed as a way to more explicitly control the amount of weight the model gives to the conditioning information, at the cost of sample diversity
# Classifier Guidance
Strat with the [[Denoising Diffusion Probabilistic Models (DDPM)#Score-Matching Langevin Dynamics (SMLD)|score-based formulation]] of a diffusion model, where our goal is to learn $\nabla \log p(\boldsymbol x_t | y)$. By [[Bayes' Theorem|Bayes' rule]], we can derive
$$
\begin{aligned}
\nabla \log p(\boldsymbol x_t | y) &= \nabla \log \left( \dfrac{p(\boldsymbol x_t)p(y| \boldsymbol x_t)}{p(y)} \right)  \\
&= \nabla \log p(\boldsymbol x_t) + \nabla \log p(y | \boldsymbol x_t) - \nabla \log p(y) \\
&= \underbrace{\nabla \log p(\boldsymbol x_t)}_{\text{unconditional score}} + \underbrace{\nabla\log p(y | \boldsymbol x_t)}_{\text{adversarial gradient}}
\end{aligned}
$$
Therefore, in Classifier Guidance, the score of an unconditional diffusion model is learned as previously derived, alongside a classifier that takes in arbitrary noisy $\boldsymbol x_t$ and attempts to predict conditional information $y$. Then, during the sampling procedure, the overall conditional score function used for annealed [[Denoising Diffusion Probabilistic Models (DDPM)#Langevin Dynamics|Langevin Dynamics]] is computed as the sum of the unconditional score function and the adversarial gradient of the noisy classifier

To introduce fine-grained control to either encourage or discourage the model to consider the conditioning information, we can scales the adversarial gradient of the noisy classifier by a $\gamma$ hyper-parameter
$$
\nabla \log p(\boldsymbol x_t | y) = \nabla \log p (\boldsymbol x_t) + \gamma \nabla \log p (y | \boldsymbol x_t)
$$
The higher $\gamma$ is, the model learns to produce samples that heavier adhere to the conditioning information, which comes at the cost of sample diversity.
![[AI-Classifier-Guidance.svg]]

Here is a pseudo-code of classifier guidance:
``` python
# Load a pre-trained image classification model, this model should be trained on images with noises 
classifier_model = ...  

# We want to generate an image of class 1, let's assume class 1 corresponds to the "cat" category  
y = 1  

# Controls the strength of the class guidance, the higher the stronger  
guidance_scale = 7.5  

# Randomly draw noise with the same shape as the output image from a Gaussian distribution  
input = get_noise(...) 

# Each step denoises the input
for t in tqdm(scheduler.timesteps):  

    # Use U-Net to predict noise (that is, the first term in the euqation above, since the score can be represented by the noise added form x_0 to x_t)  
    with torch.no_grad():  
        noise_pred = model(input, t).sample  
  
    # Classifier guidance step. Pass the input into a classifier, and get a predicted \hat{y}, then return the gradient given the ground-truth y
    class_guidance = classifier_model.get_class_guidance(input, y)
    
	# Compute gradient  
    noise_pred += class_guidance * guidance_scale  # Apply the gradient   
  
    # Calculate x_{t-1} using the updated noise  
    input = scheduler.step(noise_pred, t, input).prev_sample
```

Classifier Guidance can **only control the categories generated by the classification model.** If the classification model distinguishes 10 classes, then Classifier Guidance can only guide the diffusion model to generate those fixed 10 classes.

To solve this problem, see [[Classifier-Free Diffusion Guidance]]
