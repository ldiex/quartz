---
zotero-key: NDSC6VPX
zt-attachments:
  - "671"
title: "GLIDE: Towards Photorealistic Image Generation and Editing with Text-Guided Diffusion Models"
authors:
  - Alex Nichol
  - Prafulla Dhariwal
  - Aditya Ramesh
  - Pranav Shyam
  - Pamela Mishkin
  - Bob McGrew
  - Ilya Sutskever
  - Mark Chen
collections:
  - Generative Models > Computer Vision > Artificial Intelligence
publish-date: 2022
url: http://arxiv.org/abs/2112.10741
DOI: 10.48550/arXiv.2112.10741
---
# CLIP Guidance
Similar to [[Classifier Guidance - Diffusion Models Beat GANs on Image Synthesis|Classifier Guidance]], while using [[CLIP - Learning Transferable Visual Models From Natural Language Supervision|CLIP]] to calculate the similarity between texts and images instead of a classifier.

The denoise step of [[Denoising Diffusion Probabilistic Models (DDPM)|DDPM]] with CLIP Guidance
$$
\nabla \log p(\boldsymbol x_t | c) = \nabla \log p (\boldsymbol x_t) + \gamma \nabla \left( f(\boldsymbol x_t)\cdot g(c) \right) 
$$
where
- $c$ is the guidance condition (text)
- $f(\cdot)$ and $g(\cdot)$ are encoders to embed images and texts into the same space so that we can use dot product to calculate similarity
![[AI-CLIP-Guidance.svg]]
Pseudo-code
``` python
# Load a pre-trained CLIP model (both image and text encoders)
clip_model, preprocess = load_clip_model(...)  

# Encode the target text prompt (e.g., "a cat sitting on a tree")
text_prompt = "a cat sitting on a tree"
text_features = clip_model.encode_text(preprocess(text_prompt))  

# Controls the strength of the CLIP guidance
guidance_scale = 7.5  

# Randomly draw noise with the same shape as the output image from a Gaussian distribution  
input = get_noise(...) 

# Each step denoises the input
for t in tqdm(scheduler.timesteps):  

    # Use U-Net to predict noise (the score function is represented by the predicted noise added from x_0 to x_t)
    with torch.no_grad():  
        noise_pred = model(input, t).sample  
  
    # CLIP guidance step: pass the current image through the CLIP model to get its features
    current_image = denormalize_image(input)  # Adjust the image to the appropriate range (e.g., [0, 1])
    image_features = clip_model.encode_image(preprocess(current_image))  
    
    # Compute the direction towards the target text features
    clip_guidance = compute_clip_direction(image_features, text_features)  
    
	# Apply the gradient for CLIP guidance
    noise_pred += clip_guidance * guidance_scale  # Strengthen the alignment with the text prompt  

    # Calculate x_{t-1} using the updated noise  
    input = scheduler.step(noise_pred, t, input).prev_sample
```

where `compute_clip_direction` can be implemented as
``` python
def compute_clip_direction(image_features, text_features):
    # Normalize the features to have unit length for proper cosine similarity calculation
    image_features = image_features / image_features.norm(dim=-1, keepdim=True)
    text_features = text_features / text_features.norm(dim=-1, keepdim=True)

    # Calculate the cosine similarity between image and text features
    similarity = (image_features * text_features).sum(dim=-1)

    # Backpropagate the similarity score to get the gradient direction
    similarity_loss = -similarity  # Maximizing similarity, so we take the negative
    similarity_loss.backward()     # Compute the gradient of the loss with respect to the image

    # Get the gradient from the image features (which implicitly propagates back to the input image)
    clip_guidance = image_features.grad

    return clip_guidance
```

# GLIDE
