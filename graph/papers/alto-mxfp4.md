---
id: paper:alto-mxfp4
type: paper
title: 'Training an MoE LLM in MXFP4: How We Closed the Gap to BF16'
authors:
- 'Han Wang'
- 'Zhitao Wang'
- 'Natalia Frumkin'
- 'Xuanwu Yin'
- 'Alireza Khodamoradi'
- 'Dong Li'
- 'Emad Barsoum'
year: 2026
month: 10
arxiv_id: '2610.32229'
url: https://arxiv.org/abs/2610.32229
methods:
- method:alto-mxfp4
cites:
- paper:quartet-ii
- paper:mxfp4-mi355x
tags:
- quantization
- mxfp4
- active
---

# Training an MoE LLM in MXFP4

## Abstract Summary
FP4 train is bandwidth-cheap but quantization error can destabilize MoE optimization. ALTO is an MXFP4 recipe for GPT-OSS-20B that closes the gap to BF16.

## Key Contributions
1. ALTO MXFP4 as an active plug-in on task:fp4-hardware-training.

## Empirical Highlights
- MXFP4 GPT-OSS-20B recipe vs BF16. Does not retarget method:quartet-ii.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.32229`
- Code: `none found` (`code_status: none`).
