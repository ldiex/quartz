---
zotero-key: 37DWR89W
zt-attachments:
  - "195"
title: "PSANet: Point-wise Spatial Attention Network for Scene Parsing"
authors:
  - Hengshuang Zhao
  - Yi Zhang
  - Shu Liu
  - Jianping Shi
  - Chen Change Loy
  - Dahua Lin
  - Jiaya Jia
collections:
  - Semantic Segmentation > Computer Vision > Artificial Intelligence
publish-date: 2018
DOI: 10.1007/978-3-030-01240-3_17
---
# Idea
Apply point-wise spatial attention mechanism to scene parsing.
# Method
Let $\boldsymbol z_i$ be the newly aggregated feature at position $i$, and $\boldsymbol x_i$ be the feature representation at position $i$ in the input feature map $\textbf{X}$, then we have the following bi-directional propagation formula:
$$
\boldsymbol z_i = \dfrac{1}{N} \sum_{\forall j\in \Omega(i)}  \left[ F_{\Delta_{ij}} (\boldsymbol x_i) \boldsymbol x_j + F_{\Delta_{ji}}(\boldsymbol x_j)\boldsymbol x_i\right] 
$$
where $\forall j\in\Omega(i)$ enumerates all positions in the region of interest associated with $i$, and $\Delta_{ij}$ represents the relative location of position $i$ and $j$
## Bi-Direction Information Propagation
![[AI-PSANet-Bi-Direction-Information-Propagation.png]]
For the first term, $F_{\Delta_{ij}}(\boldsymbol x_i)$ encodes to what extent the features at other positions can help prediction. Each position *collects* information from other positions. For the second term, $F_{\Delta_{ij}}(\boldsymbol x_j)$ denotes the importance of the feature at one position to to features at other positions. Each position *distributes* information to others.

Specifically, in this model both $F_{\Delta_{ij}}(\boldsymbol x_i)$ and $F_{\Delta_{ij}}(\boldsymbol x_j)$ can be regarded as predicted attention values to aggregate feature $\boldsymbol x_j$, rewriting the formula above as
$$
\boldsymbol z_i = \dfrac{1}{N} \sum_{\forall j} \boldsymbol a_{i,j}^{\mathrm{c}} \boldsymbol x_i + \dfrac{1}{N} \sum_{\forall j} \boldsymbol a_{i,j}^{\mathrm{d}} \boldsymbol x_j
$$
where $\boldsymbol a_{i,j}^{\mathrm{ c}}$ and $\boldsymbol a_{i,j}^{\mathrm{d}}$ denote the predicted attention values in the point-wise attention maps $\textbf{A}^{\mathrm{c}}$ and $\textbf{A}^{\mathrm{d}}$ from *collect* and *distribute* branches, respectively.
# Architecture
## PSA Module
![[AI-PSANet-PSA-Module.png]]
## Attention Map Generation
![[AI-PSANet-Point-wise-Attention.png]]
In the *collect* branch, at each position $i$, with $k$-th row and $l$-th column, we predict how current position is related to other positions based on feature at position $i$. 

Specifically, element at $s$-th row and $k$-th column in the attention mask $\boldsymbol a_i^{\mathrm{c}}$ (i.e. $\boldsymbol a_{[k,l]}^{\mathrm{c}}$) is
$$
\boldsymbol{a}_{[k,l],[s,t]}^c=\boldsymbol{h}_{[k,l],[H-k+s,W-l+t]}^c,\quad\forall s\in[0,H),\quad t\in[0,W)
$$
where $[\cdot,\cdot]$ indexed position in rows and columns.
## Model
![[AI-PSANet-Arch.png]]