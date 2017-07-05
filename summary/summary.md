## A Deep Reinforced Model for Abstractive Summarization
extractive summarization (A recurrent neural network based sequence
model for extractive summarization of documents)

abstractive summarizarion (Abstractive sentence summarization
with attentive recurrent neural networks)(Abstractive text summarization
using sequence-to-sequence rnns and beyond)(Efficient summarization with
read-again and copy mechanism)

缺点:
(Abstractive text summarization
using sequence-to-sequence rnns and beyond) 运用了带有attention 的encoder-decoder 模型, 但是产生的段落里会伴有重复的信息

(Efficient summarization with
read-again and copy mechanism) 基于MT 去产发生summary 仅仅关注短的文本，并没有在更复杂的文本上进行实验.

解决了重复信息的问题
(1)运用了attention 机制(但是写的挺好) 
(2)提出了一个新的目标函数，合并最大似然的交叉熵损失和policy gradient reinforence 的rewards 




