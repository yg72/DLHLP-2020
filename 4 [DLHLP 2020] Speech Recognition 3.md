# [DLHLP 2020] Speech Recognition 3 -- CTC, RNN-T and more

### Slice: http://speech.ee.ntu.edu.tw/~tlkagk/courses/DLHLP20/ASR%20(v12).pdf
### CTC: Connectionist Temporal classification 

* Input T acoustic features, output T tokens (ignoring down sampling)
* encoder, classifier and get output
* <u>output tokens including</u> $\phi$, <u>merging duplicated tokens</u>, <u>removing $\phi$</u> 
* Alignment: all permutations

* issue: 

<img src=".\screenshot\SP3\1.PNG" alt="1" style="zoom: 67%;" />

### RNN-T: RNN Transducer :) online

* RNA: Recurrent Neural Aligner: replace CTC classifier to LSTM
* How RNN-T work?
* ![2](.\screenshot\SP3\2.PNG)
* issue: how to align $\phi$ with words
  * training another RNN: language model: ignore speech, only consider tokens, no $\phi$ in text, **<u>for training algorithm</u>**
  * <img src=".\screenshot\SP3\3.PNG" alt="3" style="zoom:67%;" />

### Neural Transducer

* Input: multi acoustic feature (window) --> attention
* <img src=".\screenshot\SP3\4.PNG" alt="4" style="zoom:67%;" />

### Monotonic Chunkwise Attention (MoChA)

* new module ('here?') to decide where the window is.
  *  dynamically shift the input window
* decode one token no $\phi$ 
![6](.\screenshot\SP3\6.png)

### Summary

![5](.\screenshot\SP3\5.png)