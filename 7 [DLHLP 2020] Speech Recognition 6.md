# [DLHLP 2020] Speech Recognition (6/7) - RNN-T Training (optional)

**** This class is difficult to understand, please review it later ****

### How to sum over all the alignments

格子的distribution不受到如何走到这个格子路径的影响

![1](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP6\1.PNG)

* 如何计算所有alignment总和？

dynamic programing 

先有RNN-T的参数才能计算alignment的结果

* training:
*  $\alpha_{i,j}$ is the summation of the scores of all the alignments that read i-th acoustic features and output j-th tokens
* $\beta_{i,j}$ is the summation of the score of all the alignments starting from i-th acoustic features and j-th tokens

![2](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP6\2.PNG)

![3](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SP6\3.PNG)