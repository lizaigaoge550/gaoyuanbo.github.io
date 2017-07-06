## Pointing the Unknown Words

用了两个softmax output layer, shortlist softmax用于计算产生在词典中的词的概率, location softmax是一个指针网络, 用于指向要拷贝的单词,

这个单词在上下文中但不在字典中.
