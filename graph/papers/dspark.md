---
id: paper:dspark
type: paper
title: 'Learning When to Commit: Schedule Distillation for Fast Diffusion Language Models'
authors:
- 'Aidar Myrzakhan'
- 'Zhiqiang Shen'
year: 2026
month: 10
arxiv_id: '2610.35804'
url: https://arxiv.org/abs/2610.35804
methods:
- method:dspark
cites:
- paper:a2d
- paper:justopd
tags:
- diffusion
- dllm
- active
---

# Learning When to Commit: Schedule Distillation for Fast Diffusion Language Models

## Abstract Summary
dLLM speed depends on which tokens to unmask so remaining positions get easier. dSpark distills unmasking schedules that reveal high-leverage tokens, with a KL regularizer. Code VILA-Lab/dSpark.

## Key Contributions
1. dSpark as an active plug-in on task:diffusion-lm-ar-delta-recycle.

## Empirical Highlights
Schedule distillation for faster parallel sampling. Does not retarget method:a2d.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.35804`
- Code: `https://github.com/VILA-Lab/dSpark (`code_status: released`).`
