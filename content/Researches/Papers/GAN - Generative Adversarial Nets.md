---
type: paper
title: Generative Adversarial Nets
tags:
  - AI
  - Generative-AI
  - GAN
author: Ian J. Goodfellow
year: "2014"
link: https://arxiv.org/abs/1406.2661
---
# Idea
The traditional way for generative models to synthesize contents is by trying to figure out the underlying mechanism of the generating process. However, why not just start with nonsenses (e.g. random noises) and train our model to improve this until the final output is so similar to a real one that no one could differentiate them?

For example, imagine running a video game which generates 60 fps 4K game graphics. If we want to train a model that generates similar game screens, instead of diving into the game code that renders the graphics and learning its way for generation, we could suppose whatever the real mechanism is, there may be just $100$ factors that determines the final output graph. By this way, we could just start with a $100$-variable Gaussian noise, and try to train our model to generate graphics from these $100$ variables. And we need to train another model to judge whether the generative outputs are similar to the real ones, which then gives the feedback to the generative model and help it to updates its parameters for better generations next time. Ideally, at last we could obtain a model that is able to generate near-real contents from any given input variables.

# Mathematical Model
To generalize, anything we see in this world could be viewed as the sampling results from a distribution over some particular data. Therefore, the generator's task is to give a distribution $p_g$ over some data $\boldsymbol x$. To learn this distribution, we define a prior on input noise variables $p_{\boldsymbol z}(\boldsymbol z)$, where $\boldsymbol z$ is some given inputs, then represent a mapping to data space as $G(\boldsymbol z;\theta_g)$. Here $G$ is a [[Differential of Mappings|differentiable]] function represented by a [[Multilayer Perceptrons|multilayer perceptron]] with parameter $\theta_g$. 

We also define a second multilayer perceptron $D(\boldsymbol x;\theta_d)$ that outputs a single scalar. $D(\boldsymbol x)$ represents the probability that $\boldsymbol x$ came form the real data rather than $p_g$. (For example, $D(\boldsymbol x)=1$ may determine $\boldsymbol x$ as real data and $D(\boldsymbol x)=0$ may suspect $\boldsymbol x$ as totally synthesized data.) 

We train $D$ to maximize the probability of assigning the correct label to both training examples and samples from $G$, that is, to maximize $\log D(\boldsymbol x)$ when $\boldsymbol x$ came form real data. And we simultaneously train $G$ to minimize the probability that $D$ recognizes the samples from $G$ were actually synthesized, that is, to minimize $\log(1-D(G(\boldsymbol z)))$. 

In consequence, $D$ and $G$ play the following two-player minimax game with value function $V(G,D)$
$$
\min_{G}\max_{D}V(D,G)=\mathbb{E}_{\boldsymbol{x}\sim p_{\text{data}}(\boldsymbol{x})}[\log D(\boldsymbol{x})]+\mathbb{E}_{\boldsymbol{z}\sim p_{\boldsymbol{z}}(\boldsymbol{z})}[\log(1-D(G(\boldsymbol{z})))]
$$
In this formula, $\boldsymbol x$ is sampled from real data distribution $p_{\mathrm{data}}(\boldsymbol x)$ and $\boldsymbol z$ is sampled from the distribution $p_{\boldsymbol z}(\boldsymbol z)$ that the generator has learned. For the discriminator $D$, the ideal case is $D(\boldsymbol x) \to 1$ and $D(G(\boldsymbol z)) \to0$, so that the right hand side approaches its maximum $0$. As for the generator $G$, the ideal case would be $D(G(\boldsymbol z)) \to1$, therefore the right side needs to be minimized. Since the final aim is to get a well-preformed $G$, we put $\underset{G}{\min}$ before $\underset{D}{\max}$. The game keeps running until we get [[Nash Equilibrium]].
