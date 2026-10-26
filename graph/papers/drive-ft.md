---
id: paper:drive-ft
type: paper
title: 'DRIVE: Fine-tuning via Data Contribution- and Diversity-aware Weighting with Prior Regularization'
authors:
- 'Qing Liu'
- 'Xinrui Chen'
- 'Yi Du'
- 'Ou Wu'
- 'Weiyao Zhu'
year: 2026
month: 10
arxiv_id: '2610.32501'
url: https://arxiv.org/abs/2610.32501
methods:
- method:drive-ft
cites:
- paper:olmo-3
tags:
- sft
- forgetting
- active
---

# DRIVE

## Abstract Summary
Single-stage FT still forgets when source data is gone. DRIVE weights samples by contribution and diversity and regularizes with a prior.

## Key Contributions
1. DRIVE as an active plug-in on task:instruct-sft-alignment.

## Empirical Highlights
- Contribution+diversity SFT weights. Does not retarget method:olmo-3.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.32501`
- Code: `https://github.com/luciabcd/DRIVE` (`code_status: released`).
