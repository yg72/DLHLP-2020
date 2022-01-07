# [DLHLP 2020] Speech Recognition 5 - Alignment of HMM, CTC and RNN-T

给一个acoustic feature 产生一个end-to-end feature

* LAS directly computes P(Y|X)
* ![1](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP5\1.PNG)

* CTC, RNN-T
*  ![2](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP5\2.PNG)
* Enumerate all the possible alignments
* ![3](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP5\3.PNG)
* HMM: Trellis Graph
* CTC
  * 如果有一样的字母中间必须插入$\phi$ 
* RNN-T
  * 第一步和最后一步必须是$\phi$

![4](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP5\4.PNG)