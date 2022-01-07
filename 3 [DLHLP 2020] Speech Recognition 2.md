# [DLHLP 2020] Speech Recognition 2

### Slice: http://speech.ee.ntu.edu.tw/~tlkagk/courses/DLHLP20/ASR%20(v12).pdf

#### LAS: 

Listen (Encoder), Attend and Spell (Decoder)  --> Seq 2 seq model

#### Listen:  (Extract content information, remove speaker variance&noises)

* input: acoustic features
* Encoder: RNN, 1D CNN * n kernel (filter can have multi layers), self-attention layers
* ![1](.\screenshot\SP2\1.PNG)
* Output: high level representations
* Down sampling (trainability): Pyramid RNN, Pooling over time -->RNN
  Time-delay DNN (CNN ~ Dilated CNN), Truncated self-attention

#### Attend (h --> c)

* Attention-->a0: Z0, match --> scalar 
  * dot-product attention: similarity
  * additive attention: add + tanh 

* softmax-->c0
* ![2](.\screenshot\SP2\2.PNG)

#### Spell (decode)

* output: distribution over all tokens (word size)
* ![3](.\screenshot\SP2\3.PNG)
* Beam search: keep B best paths at each step
  * assume there are only 2 tokens (V=2)

#### Training

* Cross entropy
* **Teacher Forcing**: use ground truth on 2nd Step
* how to use Attention --> 3 ways
* ![4](.\screenshot\SP2\4.PNG)

#### Location-aware attention

* ![5](.\screenshot\SP2\5.PNG)

#### LAS Works?

* LAS outputs the first token after listening the whole input
* users expect on-line speech recognition