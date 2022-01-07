# [DLHLP 2020] Speech Recognition 4 - HMM (optional)

### Slice: http://speech.ee.ntu.edu.tw/~tlkagk/courses/DLHLP20/ASR2%20(v6).pdf
### Hidden Markov Model (HMM)

$$
Y^*=arg maxP(Y|X)
=arg maxP(X|Y)P(Y)
$$

P(X|Y): Acoustic model (HMM)

P(Y): language model

* induce **state** (smaller than phoneme)
  * A token sequence Y corresponds to a sequence of **states S**
* Transition Probability: Probability from one state to another
* Emission Probability: too many states --> tied state
![1](.\screenshot\SP4\1.PNG)
* Subspace GMM

### Tandem: How to use Deep Learning?
* training a **State classifier** and get a new acoustic feature for HMM
* ![3](.\screenshot\SP4\3.PNG)


### DNN-HMM Hybrid

![2](.\screenshot\SP4\2.PNG)

### How to train a state classifier

* Training HMM-GMM model can get a state alignment (distribute state sequence to acoustic features), which can be replaced by DNN
* 



Appendix:

* Emission Probability: 给定一个state，这个state产生某个样子的acoustic feature的几率有多大，premise：每一个state，产生的声音信号有一个固定的distribution
* tied state：假设某些state发音一样，则共用一个Gaussian Distribution。
* DNN-HMM Hybrid: 用DNN计算P(a) 所用的state共用同一个DNN，data-driven model