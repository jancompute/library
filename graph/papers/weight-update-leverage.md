---
id: paper:weight-update-leverage
type: paper
title: 'What a Weight Update Buys: Leverage Across Training Stages'
authors:
- 'Shikhar Shiromani'
year: 2026
month: 10
arxiv_id: '2610.37719'
url: https://arxiv.org/abs/2610.37719
methods:
- method:muon2
- method:olmo-3
cites:
- paper:muon2
- paper:olmo-3
tags:
- optimizer
- gotcha
---

# What a Weight Update Buys: Leverage Across Training Stages

## Abstract Summary
Leverage is the Fisher quadratic of an update vs random directions of the same size. Pretraining windows sit at random on prose; SFT ~5x; RL-Zero/RLVR 400-1500; DPO 400-23000. bf16 without an fp32 master freezes 36-99% of coordinates. Post-training moves ~0.001 of the weight norm; pretraining ~1/3.

## Key Contributions
1. Stage-wise leverage instrument plus the bf16-no-master freeze gotcha.

## Empirical Highlights
Olmo-3 / Tulu-3 / Zephyr / OLMo-2. Does not retarget Muon2 or OLMo-3.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37719`
- Code: `none found (`code_status: none`).`
