---
zotero-key: 2I9W4BZX
zt-attachments:
  - "661"
title: Classifier-Free Diffusion Guidance
authors:
  - Jonathan Ho
  - Tim Salimans
collections:
  - Generative Models > Computer Vision > Artificial Intelligence
publish-date: 2022
url: http://arxiv.org/abs/2207.12598
DOI: 10.48550/arXiv.2207.12598
---
# Classifier-Free Diffusion Guidance
By rearranging the first equation in [[Classifier-Free Diffusion Guidance|Classifier Guidance]]
$$
\nabla \log p(y | \boldsymbol x_t) = \nabla \log p(\boldsymbol x_t | y) - \nabla \log p(\boldsymbol x_t)
$$
And substituting this into the second equation
$$
\begin{aligned}
\nabla \log p(\boldsymbol x_t | y) &= \nabla \log p(\boldsymbol x_t) + \gamma \left( \nabla \log p(\boldsymbol x_t | y) - \nabla \log p(\boldsymbol x_t)\right)  \\
&= \gamma \nabla \log p(\boldsymbol x_t | y) + (1-\gamma) \nabla \log p(\boldsymbol x_t)
\end{aligned}
$$
Once again, $\gamma$ is a term that controls how much our learned conditional model cares about the conditioning information.
![[AI-Classifier-Free-Guidance.svg]]
Another example of where the condition is text
``` python
# Load an CLIP model  
clip_model = ... 

# Input text   
text = "a dog" 

# Encode the conditional text  
text_embeddings = clip_model.text_encode(text) 

# Encode empty text  
empty_embeddings = clip_model.text_encode("") 

# Concatenate them together as the condition  
text_embeddings = torch.cat([empty_embeddings, text_embeddings]) 

# Randomly draw noise with the same shape as the output image from a Gaussian distribution  
input = get_noise(...) 
  
for t in tqdm(scheduler.timesteps):  

	# Use UNet for inference, to predict noise  
	with torch.no_grad():  
		# Here we predict noise for both images with text (for the first term) and images with empty text (for the second term), respectively
		noise_pred = model(input,t,encoder_hidden_states=text_embeddings).sample
	  
	# Split into unconditional and conditional noise  
	noise_pred_uncond, noise_pred_text = noise_pred.chunk(2) 

	# Consider the vector from "unconditional noise" towards "conditional noise",  
	# and scale this vector according to the value of guidance_scale  
	noise_pred = noise_pred_uncond + guidance_scale * (noise_pred_text - noise_pred_uncond)  
	  
	# Calculate x_t-1 using the predicted noise_pred and x_t  
	input = scheduler.step(noise_pred, t, input).prev_sample
```

In the [[U-Net|U-Net]] architecture, for examples, the text embeddings are typically concatenated with the input features at certain stages (e.g., the bottleneck or skip connections). This allows the U-Net to leverage the contextual information provided by the text when making predictions.

During training, Classifier-Free Guidance requires **training two models: one is an unconditional generation model, and the other is a conditional generation model.** However, these two models can be represented by the same model, and during training, it is only necessary to randomly set the condition to null with a certain probability.

During inference, the final result can be obtained by linear extrapolation between conditional and unconditional generation. The quality of the generated samples can be adjusted through the guidance coefficient, balancing the realism and diversity of the generated samples.
