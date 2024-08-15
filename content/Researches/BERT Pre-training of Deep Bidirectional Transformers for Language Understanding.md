---
type: paper
tags:
  - AI
  - Transformer
  - NLP
author: Jacob Devlin
year: "2019"
link: http://arxiv.org/abs/1810.04805
---
# Idea
## Previous Works
- [[ELMo]]: use *bidirectional* information(the model can access the contexts above and below) on traditional architectures ([[Recurrent Neural Networks (RNNs)|RNNs]])
- [[GPT]]: use unidirectional information (left to right in particular), on more modern architectures ([[Attention Is All You Need|transformers]])
## Innovation
Train transformers on bidirectional information

# Framework
## Steps
- **Pre-training**: the model is trained on unlabeled data over different pre-training tasks
- **Fine-tuning**: first initialize the model with the pre-trained parameters, and all of the parameters are fine-tuned using labeled data from the downstream tasks
![[AI-BERT.png]]
