---
layout: default
---

<div style="text-align: center;">
    <p style="margin: 0;">
        <strong>Tom Baker<sup>1*,2</sup></strong>
        <span style="margin-left: 1em;"></span>
        <strong>Javier Nistal<sup>1</sup></strong>
    </p>
    <p style="margin: 0;"><sup>1</sup>Sony CSL Paris</p>
    <p style="margin: 0;"><sup>2</sup>University of Manchester</p>
    <p style="margin: 0; font-size: smaller;"><sup>*</sup>Work completed during internship at Sony CSL Paris</p>
</div>

## Abstract
Text-to-audio diffusion models excel at generating high-quality, full-length musical audio with context alignment, but musicians and creators often require finer-grained, time-varying control—challenging the limitations of text prompts alone. While ControlNet enables the incorporation of generic control signals, multi-condition applications often become memory-intensive or restrict users to a fixed set of controls. In this work, we propose a novel, lightweight, and modular control methodology adapted from ControlNet, reducing the parameter count by up to 5x. Through both objective metrics and subjective evaluations, we demonstrate that our method matches the performance of ControlNet in terms of audio quality and condition adherence, while offering greater flexibility and reduced memory usage. 

---

## Architecture Overview
<div style="width: 50%; margin: 0 auto;">
    <img src="assets/LiLAC.png" alt="Architecture Diagram" style="width: 100%;">
</div>
*Here is a outline showing how the LiLAC architecture compares to ControlNet. Instead of cloning the encoder of the model we intend to append controls to, we perform a second pass through each of the models frozen encoder blocks, wrapping these by smaller convolutional layers. Specifically, we introduce three layers per block: a **head** layer before the frozen block, a **tail** layer after the frozen block, and a **residual** connection to preserve condition information as it passes through the frozen block.*

---

## Audio Examples

| Instrument | Original Sample| LiLAC H | LiLAC H+T+R | Condition |
|-|-|-|-|-|
| Electric Guitar| <audio controls src="assets/audio/10o.wav"></audio>| <audio controls src="assets/audio/10lh.wav"></audio> | <audio controls src="assets/audio/10lhtr.wav"></audio> | <img src="assets/images/10.png" style="width: 100%;"> |
| Synth Pad| <audio controls src="assets/audio/111o.wav"></audio>| <audio controls src="assets/audio/11lh.wav"></audio> | <audio controls src="assets/audio/11lhtr.wav"></audio> | <img src="assets/images/11.png" style="width: 100%;"> |
| Lead Guitar| <audio controls src="assets/audio/12o.wav"></audio>| <audio controls src="assets/audio/12lh.wav"></audio> | <audio controls src="assets/audio/12lhtr.wav"></audio> | <img src="assets/images/12.png" style="width: 100%;"> |
