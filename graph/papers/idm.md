---
id: paper:idm
type: paper
title: 'Intrinsic Distribution Matching'
authors:
- 'Deyuan Liu'
- 'Yansen Han'
- 'Kaiwen Zheng'
- 'Jun Xie'
- 'Jiacheng Liu'
- 'Zhenglin Cheng'
- 'Peng Sun'
- 'Jintao Zhang'
- 'Jianguo Li'
- 'Tao Lin'
year: 2026
month: 10
arxiv_id: '2610.39633'
url: https://arxiv.org/abs/2610.39633
methods:
- method:idm
cites:
- paper:diffusion-opsd
tags:
- diffusion
- distillation
- active
---

# Intrinsic Distribution Matching

## Abstract Summary
IDM keeps the full DMD score correction and adds an explicit Gaussian moment match (feature mean and per-coordinate std) against the generator's EMA copy, with no external encoder. Reverse-KL decomposes into a Gaussian moment term plus a residual; IDM constrains the moment term.

## Key Contributions
1. EMA-copy moment matching on top of DMD for one-/few-step T2I.

## Empirical Highlights
Z-Image-Turbo 6B and Qwen-Image 20B, full and LoRA. Two NFE: Chinese/English LongText-Bench 94.25% / 90.20%, highest among compared methods at that budget. Code github.com/inclusionAI/IDM. Does not retarget method:diffusion-opsd or method:self-opd.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.39633`
- Code: `https://github.com/inclusionAI/IDM (`code_status: released`).`
