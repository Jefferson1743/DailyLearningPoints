# Domain Gerneration 
[toc]
## Dynamically Decoding Source Domain Knowledge for Unseen Domain Generaliztion
[原文](./papers/DYNAMICALLY%20DECODING%20SOURCE%20DOMAIN%20KNOWLEDGE%20FOR%20UNSEEN%20DOMAIN%20GENERALIZATION.pdf)

### 主要思路
In this paper, we propose to adapt Transformers for the purpose of dynamically decoding source domain knowledge for domain generalization. Specifically, we build one domain-specific local expert per source domain, and one domain-agnostic feature branch as query. Then, all local-domain features will be encoded by Transformer encoders, as source domain knowledge
in memory. While in the Transformer decoders, the domain-agnostic query will
interact with the memory in the cross-attention module, where similar domains
with the input will contribute more in the attention output. This way, the source domain knowledge will be dynamically decoded for the inference of the current input from unseen domain.

### 具体实验

## Attention Is All You Need
[原文](./papers/Attention%20Is%20All%20You%20Need.pdf)

### 主要思路


### 结论
 
### 具体实验