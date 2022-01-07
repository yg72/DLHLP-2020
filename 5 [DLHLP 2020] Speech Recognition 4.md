# [DLHLP 2020] Speech Recognition 4 - HMM (optional)

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
* Subspace GMM

### Tandem

DNN-HMM Hybrid

state classifier

