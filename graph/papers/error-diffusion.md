---
id: paper:error-diffusion
type: paper
title: 'Error Diffusion Replaces Latent Weights: Training Binary-Weight Language Models on a Few Bits of Dithered State'
authors:
- 'Pierre-Olivier Bonin'
year: 2026
month: 10
arxiv_id: '2610.34566'
url: https://arxiv.org/abs/2610.34566
methods:
- method:error-diffusion
cites:
- paper:sparse-bitnet
tags:
- quantization
- 1bit
- active
---

# Error Diffusion Replaces Latent Weights: Training Binary-Weight Language Models on a Few Bits of Dithered State

## Abstract Summary
Binary-weight training usually keeps a full-precision latent plus Adam, about 96 extra bits per weight. Error diffusion keeps a 2-8-bit residual buffer and flips the bit when the residual crosses a threshold. NeurIPS 2026 SLM-Agents workshop. Code pierreolivierbonin/error-diffusion-binary-weight-lms.

## Key Contributions
1. Error diffusion as an active plug-in on task:1bit-extreme-quantization.

## Empirical Highlights
Training state per weight 97 bits to 3-9 (up to 19x). Threshold-aligned 4-bit buffers match 8-bit on a binary MLP. Does not retarget method:sparse-bitnet.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34566`
- Code: `https://github.com/pierreolivierbonin/error-diffusion-binary-weight-lms (`code_status: released`).`
