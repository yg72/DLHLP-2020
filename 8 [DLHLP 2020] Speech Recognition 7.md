# [DLHLP 2020] Speech Recognition (7/7) - Language Modeling

### Why language model?

* Language model: Estimated the probability of token sequence

  * token sequence: Y = y1,y2,......,yn
  * P(y1,y2......yn)
  * HMM:   $Y^*=arg maxP(X|Y)P(Y)$
  * LAS: seems no need for language model: $Y^*=argmaxP(Y|X)$ **(*P(Y))**
    * where P(Y|X) --> need paired data
    * P(Y) --> easy to collect
    * 如果输出是文字，加上language model P(Y)往往有用
  * BERT: 30 

* N-gram model (LM)

  * How to estimate P(y1,y2,……,yn)
  * Collect large text data as training data
    * no all kinds of sequence appear in the training data
  * N-gram language model: P(y1,y2,……,yn) = P(y1|BOS)P(y2|y1)...P(yn|yn-1) 拆分概率

* Continuous LM

  * Recommendation system
    * Matrix Factorization
    * for each token there is a vector
    * nij: 出现次数

  ![3](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP7\3.PNG)

* NN-based LM

* RNN-based LM

### How to use LM to improve LAS?

![1](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP7\1.PNG)

* shallow fusion
* deep fusion: 不能任意换language model，除非换domain的时候 
* <img src="C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP7\2.PNG" alt="2" style="zoom:75%;" />

* cold fusion: LAS and LM co-training, cannot change language model