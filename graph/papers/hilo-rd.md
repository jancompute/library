---
id: paper:hilo-rd
type: paper
title: 'HiLo-RD: Cross-Budget Self-Distillation for Masked Diffusion Language Models'
authors:
- 'Xiang Li'
- 'Chengting Yu'
- 'Jungang Li'
- 'Yilun Zheng'
- 'Junzhuo Li'
- 'Xingyao Zhang'
- 'Wenbo Su'
- 'Xuming Hu'
year: 2026
month: 10
arxiv_id: '2610.36901'
url: https://arxiv.org/abs/2610.36901
methods:
- method:hilo-rd
cites:
- paper:a2d
- paper:led
tags:
- diffusion
- dllm
- active
---

# HiLo-RD: Cross-Budget Self-Distillation for Masked Diffusion Language Models

## Abstract Summary
Small generation windows make masked dLLMs commit answer fragments too early. HiLo-RD matches hidden states from large-window teacher views onto cropped small-window student views at committed positions, with no external teacher.

## Key Contributions
1. HiLo-RD as an active cross-budget dLLM plug-in on task:diffusion-lm-ar-delta-recycle.

## Empirical Highlights
GSM8K +9.4pp with about 25% shorter readable length; math gains transfer to code. Does not retarget method:a2d.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36901`
- Code: `none found (`code_status: none`).`
