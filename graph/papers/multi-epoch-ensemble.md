---
id: paper:multi-epoch-ensemble
type: paper
title: 'A Scaling Theory of Multi-Epoch Pretraining: Late-Time Overfitting and Ensembling'
authors:
- 'Zhen Yang'
- 'Yidi Miao'
- 'Blake Bordelon'
year: 2026
month: 11
arxiv_id: '2611.03590'
url: https://arxiv.org/abs/2611.03590
methods:
- method:multi-epoch-ensemble
cites:
- paper:repeated-token-worth
- paper:data-constrained-hp-ensemble
tags:
- pretrain
- ensemble
- data-constrained
- active
---

# A Scaling Theory of Multi-Epoch Pretraining: Late-Time Overfitting and Ensembling

## Abstract Summary
When unique tokens are fixed, extra epochs overfit. FineWeb logit averaging reduces late-training deterioration, delays optimal stopping, and can beat wider or deeper single models at matched parameter-token budgets. DMFT for multi-epoch SGD in power-law random-feature ensembles yields compute-allocation laws: ensemble size should grow at least as fast as training time per member.

## Key Contributions
1. Logit-averaging ensembles plus compute-allocation laws under a unique-token budget.

## Empirical Highlights
FineWeb: logit averaging delays optimal stopping and can outperform wider/deeper singles at matched parameter-token budgets. Complementary to Repeated-Token Worth / Repetition-Count Selection / data-constrained HP ensemble.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03590`
- Code: none found (`code_status: none`).
