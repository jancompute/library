---
id: paper:wid
type: paper
title: 'Beyond the Estimate: Wiener-Informed Decoding for Easier Training of Pixel-Space Flow Models'
authors:
- 'Ziqiao Wang'
- 'Yang You'
year: 2026
month: 10
arxiv_id: '2610.36192'
url: https://arxiv.org/abs/2610.36192
methods:
- method:wid
cites:
- paper:representation-guidance
tags:
- diffusion
- pixel-dit
- active
---

# Beyond the Estimate: Wiener-Informed Decoding for Easier Training of Pixel-Space Flow Models

## Abstract Summary
Pixel-space velocity learning is eased by injecting coarse second-order image statistics into the native decoder. WiD couples a trainable patch-PCA Wiener path with coefficient interfaces that add features to the decoder and return a coefficient correction, all trained jointly under the original pixel-space velocity objective.

## Key Contributions
1. Trainable Wiener-informed pixel decoding as an active plug-in on task:pixel-diffusion-pretrain.

## Empirical Highlights
PixelDiT-XL ImageNet-256 FID 1.53 at 500 epochs vs native 1.54 at 800 (37.5% fewer epochs). ImageNet-512 FID 1.64 after 260+50 vs native 1.81 at 320+530. DeCo-XXL GenEval 0.49 vs 0.43 and DPG-Bench 78.8 vs 73.1 at 80K steps. Not a head-to-head vs Representation Guidance. Does not retarget method:representation-guidance.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36192`
- Code: `none found (`code_status: none`). Authors say training code, checkpoints, logs, and statistical priors will be released after acceptance.`
