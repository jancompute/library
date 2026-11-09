---
id: paper:sifr
type: paper
title: 'SIFR: Stable Signed Flow Reinforcement'
authors:
- Runlong Liao
- Xingqian Xu
- Lizhang Chen
- Baiyu Su
- Yufan Huang
- Zhonghao Wang
- Akash Gokul
- Ming-Yu Liu
- Qiang Liu
- Yogesh Balaji
year: 2026
month: 11
arxiv_id: '2611.09175'
url: https://arxiv.org/abs/2611.09175
methods:
- method:sifr
cites:
- paper:diffusion-opsd
- paper:self-opd
- paper:mend
tags:
- diffusion
- post-training
- flow
- active
---

# SIFR: Stable Signed Flow Reinforcement

## Abstract Summary
Iterative reward fine-tuning of flow models uses positive reward weights with no unfitting signal and concentrates the distribution until collapse. SIFR replaces those weights with signed advantages and constrains velocity drift from a reference model with a Lagrange multiplier on a prescribed drift budget. Existing flow RL methods are shown to minimize a signed loss and differ mainly in regularization. No public code as of 2026-11-09.

## Key Contributions
1. Signed advantages instead of positive reward reweighting, supplying an explicit unfitting term.
2. Lagrange-adapted velocity-drift budget vs a frozen reference.
3. Unified view of flow RL as signed-loss plus regularization choice.

## Empirical Highlights
SD3.5 Medium $2.5$B, FLUX.2 Klein $9$B, Cosmos 3 Super T2I $64$B; $12$ backbone–reward pairs (preference and rule-based). Faster peak reward; keeps improving where baselines stall or collapse. Does not retarget DiffusionOPSD / Self-OPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.09175`
- Code: none found (`code_status: none`).
