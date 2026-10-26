---
id: paper:lazyflash
type: paper
title: 'LazyFlash: Forward-Dense, Backward-Sparse Attention for Accelerated Long-Context Fine-Tuning'
authors:
- 'Keqi Deng'
- 'Ruchao Fan'
- 'Jinyu Li'
year: 2026
month: 10
arxiv_id: '2610.31911'
url: https://arxiv.org/abs/2610.31911
methods:
- method:lazyflash
cites:
- paper:sas
tags:
- sparse-attention
- finetune
- active
---

# LazyFlash

## Abstract Summary
Sparse attention is mostly an inference trick. LazyFlash keeps the forward dense and sparsifies the backward for long-context fine-tuning wall-clock.

## Key Contributions
1. LazyFlash as an active plug-in on task:posttrain-attention-sparsification.

## Empirical Highlights
- Forward-dense / backward-sparse FT. Does not retarget method:sas.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.31911`
- Code: `none found` (`code_status: none`).
