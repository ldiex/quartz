---
zotero-key: JWZGJ6FU
zt-attachments:
  - "372"
title: "OneFormer: One Transformer to Rule Universal Image Segmentation"
authors:
  - Jitesh Jain
  - Jiachen Li
  - MangTik Chiu
  - Ali Hassani
  - Nikita Orlov
  - Humphrey Shi
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2022
url: http://arxiv.org/abs/2211.06220
DOI: 10.48550/arXiv.2211.06220
---
# Idea
Propose a universal model for semantic, instance and panoptic segmentation (See [[Semantic Segmentation#Semantic vs Instance vs Panoptic|differences]]), which just requires once-and-for-all training.
- Introduce a task token to condition the model on the task at hand
- Use a query-text contrastive loss

# Architecture
![[AI-OneFormer-Arch.png]]
## Multi-Scale Feature Modeling
 Extract **multi-scale features** for an input image using a backbone, followed by a pixel decoder (translating the high-level features into pixel-level predictions)
## Unified Task-Conditional Query Formulation
### Task Input Token
Uniformly sample `{task}` from `{panopitc, instance, semantic}` to form the task input token

At the same time, uniformly sample the corresponding **ground truth** to generate text queries $\textbf{Q}_{\text{text}}$
### Text Query ($\textbf{Q}_\text{text}$)
As shown below, first iterate over the set of masks to create a list of text ($\textbf{T}_\text{text}$) with a template `a photo with a {CLS}`. Then pad $\textbf{T}_\text{text}$ with `a/an {task}` entries to obtain a padded list ($\textbf{T}_\text{pad}$) of constant length $N_\text{text}$, with padded entries representation `no-object` masks.
![[AI-OneFormer-Input-Text-Formation.png]]
To obtain the text queries $\textbf{Q}_\text{text}$, we first tokenize the text entries $\textbf{T}_\text{pad}$ and pass the tokenized representation through a text-encoder, which is a $6$-layer transformer. The encoded $N_\text{text}$ text embeddings represent the number of binary masks and their corresponding classes in the input image. We further concatenate a set of $N_\text{ctx}$ learnable text context embeddings $\textbf{Q}_\text{ctx}$ to the encoded text embeddings to obtain the final $N$ text quires $\textbf{Q}_\text{text}$
![[AI-OneFormer-Text-Mapper.png]]
 The goal of $\textbf{Q}_\text{ctx}$ is to provide a *unified textual context* that captures the relevant information necessary for various tasks, such as image segmentation.
### Object Query ($\textbf{Q}$)
First initialize the object queries ($\textbf{Q}'$) as $N-1$ times repetitions of the task-token $\textbf{Q}_\text{task}$. Then update $\textbf{Q}'$ with guidance from the flattened $\dfrac{1}{4}$-scale features inside a $2$-layer transformer.  The updated $\textbf{Q}'$ from the transformer (rich with image-contextual information) is concatenated with $\textbf{Q}_\text{task}$ to obtain a task-conditioned representation of $N$ queries, $\textbf{Q}$
### Query-Task Contrastive Loss
Considering that we have a batch of $B$ object-text query pairs $\left\{ (q_i^\text{obj}, q_i^\text{txt}) \right\}_{i = 1}^B$, where $q_i^\text{obj}$ and $q_i^\text{txt}$ are the corresponding object and text queried, respectively, of the $i$-th pair, we measure the similarity between the queries by calculating a dot product.
$$
\begin{aligned}
\mathcal L_{\textbf{Q} \to \textbf{Q}_\text{text}} &= -\dfrac{1}{B} \sum_{i = 1}^B \log \dfrac{\exp \left( q_i^\text{obj} \odot q_i^\text{txt} /\tau\right) }{\sum_{j = 1}\exp \left( q_i^\text{obj} \odot q_j^\text{txt} /\tau\right)} \\
\mathcal L_{\textbf{Q}_\text{text} \to \textbf{Q}} &= -\dfrac{1}{B} \sum_{i = 1}^B \log \dfrac{\exp \left( q_i^\text{txt} \odot q_i^\text{obj} /\tau\right) }{\sum_{j = 1}\exp \left( q_i^\text{txt} \odot q_j^\text{obj} /\tau\right)} \\
\mathcal L_{\textbf{Q} \leftrightarrow  \textbf{Q}_\text{text}} &= \mathcal L_{\textbf{Q} \to \textbf{Q}_\text{text}} + \mathcal L_{\textbf{Q}_{text} \to \textbf{ Q}}
\end{aligned}
$$
Here $\tau$ is a learnable temperature parameter to scale the contrastive logits. 
