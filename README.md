# DLHLP-2020

This is notes on speech parts of [DLHLP-2020] by Hung-yi Lee. 

The videos can be found here: https://www.youtube.com/playlist?list=PLJV_el3uVTsO07RpBYFsXg-bN5Lu0nhdG.

## Papers to read

* Recursive speech separation for unknown number of speakers  

* UTTERANCE-LEVEL AGGREGATION FOR SPEAKER RECOGNITION IN THE WILD -- NetVLAD [Xie, et al., ICASSP’19] Extract only the certain part of the long signal

* Voice Conversion for data augmentation 

  * man <=> woman: Measuring the Effectiveness of Voice Conversion on Speaker Identification and Automatic Speech Recognition Systems, Keskin et al., 2019 (not always useful)
  * Transfer clean sound into noisy sound: Cross-domain Speech Recognition Using Nonparallel Corpora with Cycle-consistent Adversarial Networks [Mimura, et al., ASRU 2017]

* speech enhancement & speech separation (not necessarily good for final results)

  * Speech enhancement

    * human [Fu, et al., ICML’19]: MetricGAN: Generative Adversarial Networks based Black-box Metric Scores Optimization for Speech Enhancement
    * machine [Shon, et al., INTERSPEECH’19]: VoiceID Loss: Speech Enhancement for Speaker Verification

  * Speech separation

    * Unknown number of speaker [Takahashi, et al., INTERSPEECH 19] -- extract one speaker once
      Recursive speech separation for unknown number of speakers

    * Multiple Microphones [Luo, et al., ASRU'19]

      FASNET: LOW-LATENCY ADAPTIVE BEAMFORMING FOR MULTI-MICROPHONE AUDIO PROCESSING

* Prosody: Towards End-to-End Prosody Transfer for Expressive Speech Synthesis with Tacotron  [Skerry-Ryan, et al., ICML’18]'

* Speaker Embedding: 

  * Transfer Learning from Speaker Verification to Multispeaker Text-To-Speech Synthesis [Jia, et al., NeurIPS’18]
  * [Wang, et al., ICML’18] **Style Tokens**: Unsupervised Style Modeling, Control and Transfer in End-to-End Speech Synthesis
