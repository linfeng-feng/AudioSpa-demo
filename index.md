
# AudioSpa: Spatializing Sound Events with Text

<!-- [![arXiv](https://img.shields.io/badge/arXiv-2402.17455-brightgreen.svg?style=flat-square)](https://arxiv.org/abs/2402.17455) -->



## Abstract

Text-to-audio (TTA) systems have recently demonstrated strong performance in synthesizing monaural audio from text. However, previous studies have yet to explore binaural spatial audio, which provides a more immersive auditory experience by incorporating the sense of spatiality. In this work, we introduce text-guided binaural audio generation. As an early effort, we focus on scenarios with a monaural reference audio and aim to associate specific sound events with their directions, thereby creating binaural spatial audio. The challenge lies in the complexity of textual descriptions and the limited availability of single-source sound event datasets. To address this, we propose AudioSpa, an end-to-end model that processes both acoustic and spatial information. We employ fusion multi-head attention (FMHA) to integrate text tokens, enhancing the generation model's multimodal learning capability. Additionally, we propose a binaural source localization model to assess the quality of the generated audio. Finally, we design a data augmentation strategy to generate diverse datasets, ensuring the model learns to spatialize sound events across various spatial positions. In the experiments, the datasets are built using multiple sound event datasets and real-world head-related transfer functions (HRTFs). Experimental results demonstrate that our model accurately places sounds at the specified locations, achieving competitive performance in both localization accuracy and signal distortion.


## Demos

<figure style="text-align: center;">
  <img src="fig\azimuth.png" alt="The figure cannot be displayed." title="The direction represented by the azimuth angle.">
  <figcaption>Fig. 1  The direction represented by the azimuth angle.</figcaption>
</figure>

We present generation results from our proposed **AudioSpa** across multiple conditions. Fig. 1 illustrates the directional angles referenced in this work, where 0 degrees corresponds to the front of the listener, 90 degrees to the left, and so on.

## A sound source in clean environments
Since the experimental setup with a sound source in clean environments is relatively simple, we only use a single sound to make comparisons. We selected a violin song, evenly segmenting the entire track and placing the segments uniformly from 0 to 360 degrees. Listeners can use this to experience the directionality described in Fig. 1. The baseline is simulated using HRIR.

<style>
  table {
    margin: auto;
    border: 0px solid black; /* 可选，给表格添加边框 */
  }
</style>


<table>
  <thead>
    <tr>
      <th>Mono</th>
      <th>Baseline</th>
      <th>AudioSpa</th>       
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_clean\violin.flac"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_clean\violin_simu.flac"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_clean\violin_h.flac"></audio></html></td>
    </tr>
    
  </tbody>
</table>

## A sound source in noisy environments
The baseline is simulated using HRIR. Previous methods typically place all sound events in a single direction. By using text captions, AudioSpa can control the direction of specific sound event.

<table>
  <thead>
    <tr>
      <th>Mono</th>
      <th>Baseline</th>
      <th>AudioSpa</th>       
    </tr>
  </thead>
  <tbody>
    <tr>
      <td colspan="3">At 250 degrees, the sound of drums breaks through the quiet.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\4151.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\4151.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\4151.wav"></audio></html></td>
    </tr>
    <tr>
      <td colspan="3">A faint run can be heard approaching from 270 degrees.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\271.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\271.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\271.wav"></audio></html></td>
    </tr>
    <tr>
      <td colspan="3">bass echoes from the 130 degrees angle.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\3990.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\3990.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\3990.wav"></audio></html></td>
    </tr>
    <tr>
      <td colspan="3">camera can be distinctly heard from 90 degrees.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\305.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\305.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\305.wav"></audio></html></td>
    </tr>
    <tr>
      <td colspan="3">From the 210 degrees angle, the wind instrument and woodwind instrument steadily increases in volume.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\2800.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\2800.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\2800.wav"></audio></html></td>
    </tr>
    <tr>
      <td colspan="3">From 140 degrees, the music resonates sharply.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\4719.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\4719.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\4719.wav"></audio></html></td>
    </tr>
    <tr>
      <td colspan="3">piano emerges from 140 degrees.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\670.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\670.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\670.wav"></audio></html></td>
    </tr>
    <tr>
      <td colspan="3">The sound of rattle (instrument) resonates at 240 degrees.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\2408.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\2408.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\2408.wav"></audio></html></td>
    </tr>
    <tr>
      <td colspan="3">You hear a distant wind instrument and woodwind instrument originating from 250 degrees.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\2645.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\2645.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\2645.wav"></audio></html></td>
    </tr>
    <tr>
      <td colspan="3">You hear the sound of guitar coming from 280 degrees.</td>
    </tr>
    <tr>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\mono\1493.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\simulation\1493.wav"></audio></html></td>
      <td><html><audio controls style="width: 200px;"><source src="1_noisy\binaural_h\1493.wav"></audio></html></td>
    </tr>
    
  </tbody>
</table>





