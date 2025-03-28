---
layout: default
---

## Abstract
Text-to-audio diffusion models produce high-quality and diverse music but lack fine-grained, time-varying controls, which are essential for music production. ControlNet enables attaching external controls to a pre-trained generative model by cloning and fine-tuning its encoder on new conditionings. However, this approach incurs a large memory footprint and restricts users to a fixed set of controls. We propose a lightweight, modular architecture that considerably reduces parameter count while matching ControlNet in audio quality and condition adherence. Our method offers greater flexibility and significantly lower memory usage, enabling more efficient training and deployment of independent controls. We conduct extensive objective and subjective evaluations, see complete paper for more details.

---

## Architecture Overview
<div style="width: 50%; margin: 0 auto;">
    <img src="assets/LiLAC.png" alt="Architecture Diagram" style="width: 100%;">
</div>
Here is a outline showing how the LiLAC architecture compares to ControlNet. Instead of the cloning encoder blocks of the backbone model we intend to append controls to, we instead  perform a second pass through each of the models frozen encoder blocks, wrapped by smaller convolutional layers. Specifically, we introduce three layers per block: 
- a *Head* layer before the frozen block 
- a *Tail* layer after the frozen block 
- a *Residual* connection to preserve condition information as it passes through the frozen block
This design achieves a significant reduction in parameters while maintaining comparable performance to the original ControlNet implementation. Utilising Diff-a-Riff as our backbone model, our lightest configuration using only head layers (LiLAC<sup>H</sup>) consists of only 32M parameters compared to ControlNet's 165M parameters.


---

## Audio Examples
This page presents a collection of audio examples that demonstrate the capabilities of our proposed LiLAC architecture in comparison to traditional approaches. Each example consists of a 10-second audio segment generated using Diff-a-Riff as the backbone model, with a Classifier-Free Guidance (CFG) value of 0.25, 30 inference steps, and CLAP embedding for text conditioning.

For comprehensive comparison, we provide the following versions of each example:
- The original reference stem
- Output generated using the standard ControlNet architecture
- Output generated using our lightweight LiLAC<sup>H</sup> configuration
- Output generated using our optimal LiLAC<sup>HTR</sup> configuration
- Output generated without additional control conditioning (Unconditioned)

We provide examples from both conditions used in the paper - Chord and Chroma conditioning. We provide a brief description below, for more information, please check out the paper linked at the top of the page.

###Chord
For the chord conditioning examples, we extracted chord progressions from complete multitrack recordings (panned to the right in the audio examples). These chord progressions were then used to guide the generation of a complementary stem, with instrument classification informed by the CLAP embedding of the target stem.

<table>
  <thead>
    <tr>
      <th>Instrument</th>
      <th>Original Sample</th>
      <th>LiLAC H</th>
      <th>LiLAC H+T+R</th>
      <th>Condition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Electric Guitar</td>
      <td><audio controls src="assets/audio/10o.mp3" class="small-audio"></audio></td>
      <td><audio controls src="assets/audio/10lh.mp3" class="small-audio"></audio></td>
      <td><audio controls src="assets/audio/10lhtr.mp3" class="small-audio"></audio></td>
      <td><img src="assets/images/10.png" style="width: 100%;"></td>
    </tr>
    <tr>
      <td>Synth Pad</td>
      <td><audio controls src="assets/audio/11o.mp3" class="small-audio"></audio></td>
      <td><audio controls src="assets/audio/11lh.mp3" class="small-audio"></audio></td>
      <td><audio controls src="assets/audio/11lhtr.mp3" class="small-audio"></audio></td>
      <td><img src="assets/images/11.png" style="width: 100%;"></td>
    </tr>
    <tr>
      <td>Lead Guitar</td>
      <td><audio controls src="assets/audio/12o.mp3" class="small-audio"></audio></td>
      <td><audio controls src="assets/audio/12lh.mp3" class="small-audio"></audio></td>
      <td><audio controls src="assets/audio/12lhtr.mp3" class="small-audio"></audio></td>
      <td><img src="assets/images/12.png" style="width: 100%;"></td>
    </tr>
  </tbody>
</table>


###Chroma
The chroma conditioning examples utilize chromagrams extracted directly from individual stems. The models attempt to recreate audio with similar pitch content based on these chromagrams.
