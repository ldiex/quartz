---
type: paper
title: "Swin Transformer: Hierarchical Vision Transformer using Shifted Windows"
tags:
  - AI
  - Computer-Vision
  - Transformer
author: Ze Liu
year: "2021"
link: http://arxiv.org/abs/2103.14030
---
# Idea
The "SW" in "Swin" stands for **Shifted Windows**.
## Issues with traditional vision transformer
- **The scale of visual entities may vary**: in a image there might be targets with different sizes but represent the same semantic value such as a person. 
- **Difficulties with high-resolution pictures**: the traditional $16 \times 16$ patches may result in exploded sequence size when tacking with high-resolution pictures.
## Shifted windows
- **Window**: Only compute self-attention in the selected window. For example, in the last layer of figure (a) below, the whole picture is sliced into $16$ windows, and each window have $16$ $4 \times 4$ pixels patches. The model views a window as a sequence and calculate the self-attention scores inside the window. After this, every non-overlapping $4$ patches in the neighborhood are concatenated, as well as the windows. Therefore we can calculate self-attention in these windows once again.
![[AI-Swin-Transformer-Window.png]]
- **Shift**: Shift the windows across layers to realize cross-windows connection. In the following figure, the windows are shifted by $2$ patches rightward and $2$ patches downward from layer $l$  to layer $l + 1$
![[AI-Swin-Transformer-Shifting.png]]
# Model
![[AI-Swin-Transformer-Arch.png]]
1. Convert Image to patches
2. Stage $1$
	1. Create embedding vectors for each patch from its original pixels
	2. **Swim Transformer Block** (the shape of outputs is the same as inputs) ($\times 2$)
		1. Apply layer normalization
		2. Calculate Windowed (**Shifted in the second block**) Multi-head Self Attention
		3. Add the attention scores to the input
		4. Apply layer normalization
		5. MLP feed-forward layer
		6. In the first block, pass the output as the input of the second block
3. Stage $2$
	1. **Patch Merging**
		1. Let the input size be $H \times W \times C$, if apply dilation $1$, for example, we label $1, 2, 3, 4$ to a $4 \times 4$ patches input, and then merge the patches with the same label to obtain $4$ $2 \times 2$-patch tensors (in general, $4$ $\dfrac{H}{2} \times \dfrac{W}{2} \times C$ tensors)
		2. Concatenate these $4$ tensors into a $\dfrac{H}{2} \times \dfrac{W}{2} \times 4C$ tensor
		$$
		\begin{bmatrix}
		1 & 2 & 1 & 2 \\
		3 & 4 & 3 & 4 \\
		1 & 2 & 1 & 2 \\
		3 & 4 & 3 & 4
		\end{bmatrix} \longrightarrow
		\begin{bmatrix}
		1 & 1 \\ 1 & 1
		\end{bmatrix} \ ; 
		\begin{bmatrix}
		2 & 2 \\ 2 & 2
		\end{bmatrix} \ ;
		\begin{bmatrix}
		3 & 3 \\ 3 & 3
		\end{bmatrix} \ ;
		\begin{bmatrix}
		4 & 4 \\ 4 & 4
		\end{bmatrix} \longrightarrow
		\begin{bmatrix}
		(1,2,3,4) & (1,2,3,4) \\
		(1,2,3,4) & (1,2,3,4)
		\end{bmatrix}
		$$
		3. Project to a $\dfrac{H}{2} \times \dfrac{W}{2} \times 2C$ tensor as the output via $1 \times 1$ convolutions
	2. Swim Transformer Block ($\times 2$)
4. Stage $3$: cut the $H, W$ to its half size and double the channel number
5. ...