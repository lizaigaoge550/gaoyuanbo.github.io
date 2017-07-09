## Long Short-Term Memory-Networks for Machine Reading

### LSTM的问题
* given the current state ht, the next state ht+1 is conditionally independent of states h1 ···ht−1 and tokens x1 ··· xt. 
While the recursive state update is performed in a Markov manner, it is assumed that LSTMs maintain unbounded memory
(i.e., the current state alone summarizes well the tokens it has seen so far). This assumption may fail in practice, 
for example when the sequence is long or when the memory size is not large enough. Another undesired property of LSTMs concerns modeling
structured input.

*  An LSTM aggregates information on a token-by-token basis in sequential order, but there is no explicit mechanism for reasoning over
structure and modeling relations between tokens
