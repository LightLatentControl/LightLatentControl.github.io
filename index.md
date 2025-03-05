---
layout: default
custom_css: assets/style.css
---

# LiLAC: A Lightweight Latent ControlNet for Musical Audio Generation

**Authors**: Tom Baker, Javier Nistal  
**Institution**: University of Manchester, SonyCSL 


## Abstract
Text-to-audio diffusion models excel at generating high-quality, full-length musical audio with context alignment, but musicians and creators often require finer-grained, time-varying control—challenging the limitations of text prompts alone. While ControlNet enables the incorporation of generic control signals, multi-condition applications often become memory-intensive or restrict users to a fixed set of controls. In this work, we propose a novel, lightweight, and modular control methodology adapted from ControlNet, reducing the parameter count by up to 5x. Through both objective metrics and subjective evaluations, we demonstrate that our method matches the performance of ControlNet in terms of audio quality and condition adherence, while offering greater flexibility and reduced memory usage. 

---

## Architecture Overview
![Architecture Diagram](assets/LiLAC.png)
*Caption for your architecture diagram*

---

## Audio Examples

| Example # | Description                                  | Audio File                     |
|-----------|----------------------------------------------|--------------------------------|
| 1         | Example 1 description                        | <audio controls src="assets/audio/example1.wav"></audio> |
| 2         | Example 2 description                        | <audio controls src="assets/audio/example2.wav"></audio> |
| 3         | Example 3 description                        | <audio controls src="assets/audio/example3.wav"></audio> |
{:.audio-table}
