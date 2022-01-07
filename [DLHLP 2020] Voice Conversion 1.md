# [DLHLP 2020] Voice Conversion (1/2) - Feature Disentangle

### Voice conversion: input speech and output speech

* What is preserved both input and output? Content

* What is changed? Speaker, speaking style(emotion,normal-to-lombard,whisper-to-normal), improving intelligibility, data augmentation

  READ THOSE TWO PAPER FOR DATA AUGMENTATION

  <img src="C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\VC1\1.PNG" alt="1" style="zoom:67%;" />

* application: Deep Fake

* In real implementation

  * premise: input and output have the same length
  * **requiring Vocoder to transfer acoustic feature to waveform**
    * Rule-based: Griffin-Lim algorithm
    * Deep Learning: WaveNet

* Categories

  * Parallel Data

    * Lack of training data:
      * Model Pre-training [Huang, et al., arXiv 19]
      * Synthesized data [Biadsy, et al., INTERSPEECH 19]

  * Unparallel Data: acoustic style transfer

    * **feature disentangle**
      * speech --> content encoder & speaker encoder
      * pre-training encoders
        * One-hot vector for each speaker (Issue: difficult to consider new speakers)
        * Speaker embedding (i-vector, d-vector, x-vector) --> speaker feature
        * content encoder: speech recognition
          * adversarial training: speaker classifier and content encoder co-training
        * Add instance normalization (IN) in content encoder to **remove speaker information**
          * Instance Normalization (IN): channel normalization
            why? filter is 
      * <img src="C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\VC1\2.PNG" alt="2" style="zoom:50%;" />
        * Decoder: add adaptive instance normalization (only influence speaker information)
        * adaptive instance normalization(AdaIN):
          * <img src="C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\VC1\3.PNG" alt="3" style="zoom:50%;" />
        * Training:
          * content encoder and speaker encoder have same input, 
          * not consider voice conversion
        * Testing: low quality
        * --> 2nd stage training:
          * input content encoder and speaker encoder with different speakers
          * train **discriminator** --> real or generated
          * train **speaker classifier** --> which speaker?
          * Patcher: help to train decoder
          * ![4](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\VC1\4.PNG)
    * **Direct Transformation** 
      * Cycle GAN (Issue: if there are N speakers, you need N*(N-1) generaotrs)
      * Generator: transfer speaker X to speaker Y
      * Discriminator: discriminate input is from speaker X
      * <img src="C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\VC1\5.PNG" alt="5" style="zoom:50%;" />
      * StarGAN (reduce network)
        * generator: input speaker $s_j$ 
        * discriminator: multi-input
        * <img src="C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\VC1\6.PNG" alt="6" style="zoom:50%;" />
      * BLOW

    