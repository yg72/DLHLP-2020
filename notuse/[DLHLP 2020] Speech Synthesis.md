# [DLHLP 2020] Speech Synthesis (1/2) - Tacotron

Text-to-Speech (TTS) Synthesis

### Outline

*  TTS before end-to-end

  * VODER
  * IBM computer 1961
  * Concatenative Approach: pick up speeches from a large database
  * Parametric Approach (HTS:HMM )
  * Deep Voice

* Tacotron: End-to-end TTS (Towards end-to-end speech synthesis)

  * Tacotron: input character, Output: spectrogram 

  * <img src="C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SSy\1.PNG" alt="1" style="zoom:50%;" />

    * Seq2Seq model + attention
    * **encoder** ~ grapheme-to-phoneme CBHG
    * **Attention**: the output audio and input text much be monotonic aligned
    * **decoder**: mel-spectrogram, generating r frames each time
      * 通过产生r个frames each time使得sequence长度减少三倍 decode sequence 长度减少，减少训练时间
      * decoder: require teacher forcing, but dropout acts like schedule sampling
      * classifier: 
    * Post processing: two loss: 
      * RNN decoder is mel-spectrogram with ground truth. 
      * CBHG with ground truth mel/linear-spectrogram (global)
      * vocoder: mel-spectrogram --> speech signal (Griffin-Lim in v1, Wavenet in V2)

  * First Step Towards End-to-end Parametric TTS Synthesis: input: phoneme, Output: acoustic features for STRAIGHT(Vocoder)

  * Char2wav: Input: character, Output: acoustic features for sampleRNN(vocoder)

  * Evaluation: MOS

  * **WaveNet: acoustic feature and ground truth waveform**

  * #### Tacotron in inference phase needs dropout! 

    * output is not distribution

  * GPT2 not most likely word as output

  * NLG: output is distribution

* Beyond Tacotron

  * Tacotron: Mispronunciation
    * Speech synthesis corpus: VCTK, LJ speech, Nancy, LibriTTS dataset 585 hours
    * using a lexicon to transform word to phoneme, and using phoneme as Tacotron input
    * character and phoneme hybrid input [Ping, et al.. ICLR 18]
  * Syntactic information [Guo, et al., INTERSPEECH 19]
  * BERT embedding as input
  * Attention: diagonal
  * ![2](C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SSy\2.PNG)
    * add regularization in Attention 
    * Monotonic Attention
    * Location-aware attention
    * More Attention: [Battenberg, et al., ICASSP 2020] 有的attention会坏掉 character error rate
  * Fast Speech & Duration informed attention Network (DurIAN) 
    * not seq 2 seq
    * encoder -- duration model: predict and add character length -- decoder -- Mel-spectrogram
    * How to train this model?
      duration is non-differentiable 
      during the training phase: using ground truth (alignment from another model)
    * <img src="C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SSy\3.PNG" alt="3" style="zoom:50%;" />
  * Dual learning: TTS v.s. ASR
    * <img src="C:\Users\gengyw\Documents\GitHub\DLHLP-2020\screenshot\SSy\4.PNG" alt="4" style="zoom:50%;" />



* Controllable TTS

  * Who is speaking：

    * Synthesize speech for a specific person (voice cloning)
    * Lack of high quality single speaker data to train a speech synthesis system

  * How to say

    * Intonation (语调), Stress (重音）, Rhythm（韵律）

    * Prosody: the variation in speech signals that remains after accounting for variation due to phonetics, speaker identity, and channel effects

    * **Speaker Embedding!** : learn speakers' property [Jia, et al., NeurIPS 18]

    * **GST-Tacotron!**: GST -- global style tokens

    * Reference audio -- **feature extractor** (dedicated architecture to avoid content copy)

      * Reference audio -- encoder -- output is not feature, but attention weight, adds with vector set -- linear combination 

    * What does the tokens effect?

    * Two-stage Training: TTS -- ASR (attention consistency)

    * GST-Tacotron 

    * property or speaker? speaker identity?  token style 

      