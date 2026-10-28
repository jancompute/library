---
id: paper:rescom
type: paper
title: 'ResCom: Activation Residual Compensation for Large Language Model Quantization'
authors:
- 'Ning Yang'
- 'Bohan Cui'
- 'Zhuowen Liu'
- 'Yuting Wang'
year: 2026
month: 10
arxiv_id: '2610.35955'
url: https://arxiv.org/abs/2610.35955
methods:
- method:rescom
cites:
- paper:quartet-ii
- paper:dualquant
tags:
- quantization
- ptq
- active
---

# ResCom: Activation Residual Compensation for Large Language Model Quantization

## Abstract Summary
Activation rounding after W+A calibration still aliases values in the same bin. ResCom adds a low-rank correction from the rounding residual, selected by output-aware calibration, with no gradient training.

## Key Contributions
1. ResCom as an active PTQ residual plug-in on task:fp4-hardware-training.

## Empirical Highlights
Llama-3-8B W4A4 rank-32: PPL 7.708 to 7.147, GSM8K 23.96 to 36.16. Does not retarget method:quartet-ii.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.35955`
- Code: `none found (`code_status: none`).`
