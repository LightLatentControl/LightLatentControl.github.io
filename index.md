---
layout: default
---

<div style="text-align: center;">
    <p style="margin: 0;"><strong>Tom Baker<sup>1,2,*</sup></strong>, <strong>Javier Nistal<sup>1</sup></strong></p>
    <p style="margin: 0;"><sup>1</sup>Sony CSL Paris</p>
    <p style="margin: 0;"><sup>2</sup>University of Manchester</p>
    <p style="margin: 0; font-size: smaller;"><sup>*</sup>Work completed during internship at Sony CSL Paris</p>
</div>

[![arXiv](https://img.shields.io/badge/arXiv-1234.5678-b31b1b.svg)](https://arxiv.org/abs/1234.5678)

## Abstract
Text-to-audio diffusion models excel at generating high-quality, full-length musical audio with context alignment, but musicians and creators often require finer-grained, time-varying control—challenging the limitations of text prompts alone. While ControlNet enables the incorporation of generic control signals, multi-condition applications often become memory-intensive or restrict users to a fixed set of controls. In this work, we propose a novel, lightweight, and modular control methodology adapted from ControlNet, reducing the parameter count by up to 5x. Through both objective metrics and subjective evaluations, we demonstrate that our method matches the performance of ControlNet in terms of audio quality and condition adherence, while offering greater flexibility and reduced memory usage. 

---

## Architecture Overview
<div style="width: 50%; margin: 0 auto;">
    ![Architecture Diagram](assets/LiLAC.png)
</div>
*Here is a outline showing how the LiLAC architecture compares to ControlNet. Instead of cloning the encoder of the model we intend to append controls to, we perform a second pass through each of the models frozen encoder blocks, wrapping these by smaller convolutional layers. Specifically, we introduce three layers per block: a **head** layer before the frozen block, a **tail** layer after the frozen block, and a **residual** connection to preserve condition information as it passes through the frozen block.*

---

## Audio Examples

| Example # | Description                                  | Audio File                     |
|-----------|----------------------------------------------|--------------------------------|
| 1         | Example 1 description                        | <audio controls src="assets/audio/example1.wav"></audio> |
| 2         | Example 2 description                        | <audio controls src="assets/audio/example2.wav"></audio> |
| 3         | Example 3 description                        | <audio controls src="assets/audio/example3.wav"></audio> |
{:.audio-table}
