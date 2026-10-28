---
id: paper:tdlm
type: paper
title: 'TDLM: Adaptive Temporal Integration for Diffusion Language Models'
authors:
- 'Bohang Sun'
- 'Max Zhu'
- 'Francesco Caso'
- 'Christopher Irwin'
- 'Jialin Yu'
- 'Pietro Liò'
year: 2026
month: 10
arxiv_id: '2610.36940'
url: https://arxiv.org/abs/2610.36940
methods:
- method:tdlm
cites:
- paper:a2d
- paper:led
tags:
- diffusion
- dllm
- active
---

# TDLM: Adaptive Temporal Integration for Diffusion Language Models

## Abstract Summary
Masked dLLMs recompute unresolved-token representations every step. TDLM adds causal temporal self-conditioning over each position's hidden history in a frozen denoiser (~0.84% parameters on LLaDA).

## Key Contributions
1. TDLM as an active temporal-self-conditioning plug-in on task:diffusion-lm-ar-delta-recycle.

## Empirical Highlights
Up to 7.15x faster generation vs original LLaDA/Dream denoisers. Does not retarget method:a2d.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36940`
- Code: `none found (`code_status: none`).`
