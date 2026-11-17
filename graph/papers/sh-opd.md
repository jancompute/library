---
id: paper:sh-opd
type: paper
title: 'Rethinking Supervision Scaling in On-Policy Distillation: From Dense Supervision to Stochastic Horizons'
authors:
- Xinhao Yao
- Zhenxing Dou
- Yong Liu
year: 2026
month: 11
arxiv_id: '2611.20687'
url: https://arxiv.org/abs/2611.20687
methods:
- method:sh-opd
cites: []
tags:
- opd
- horizon
- efficiency
- active
---

# Rethinking Supervision Scaling in On-Policy Distillation: From Dense Supervision to Stochastic Horizons

## Abstract Summary
Dense full-sequence OPD is expensive. SH-OPD samples a shared horizon per batch for parallel generation. Characterizes reweighting bias and a compute-reweighting trade-off. Slightly higher math accuracy at ~45% of full-OPD per-update cost; competitive code at ~60%. Work in progress. Code chen123CtrlS/SH-OPD. Distinct from Flash-OPD. Does not retarget OPD.

## Key Contributions
1. Shared-batch stochastic horizons instead of dense full-sequence OPD.
2. Reweighting-bias characterization under truncated horizons.
3. Parallel generation without per-sequence horizon scheduling.

## Empirical Highlights
Math ~45% cost, slightly higher accuracy. Code ~60% cost, competitive.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.20687`
- Code: `https://github.com/chen123CtrlS/SH-OPD` (`code_status: released`).
