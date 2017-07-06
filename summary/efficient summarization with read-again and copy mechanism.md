## Efficient Summarization With Read-again And Copy Mechanism

### 以往总结的两个缺点

(1) encoder在计算每个单词的representation，只考虑了已经读的单词的历史

(2) OOV

### 解决办法

(1) 首先读取输入的序列, 在计算这个单词的representation之前

(2) 简单的copy机制
