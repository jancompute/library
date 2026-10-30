---
id: paper:data-constrained-hp-ensemble
type: paper
title: 'Improving Data-Constrained Scaling with Hyperparameter Transfer and Ensembling'
authors:
- 'Ethan Baron'
- 'Shmuel Berman'
- 'Anirudh Satheesh'
- 'Akshay Vegesna'
- 'Samip Dahal'
- 'Andrew Gordon Wilson'
year: 2026
month: 10
arxiv_id: '2610.37842'
url: https://arxiv.org/abs/2610.37842
methods:
- method:data-constrained-hp-ensemble
cites:
- paper:repeated-token-worth
tags:
- data-constrained
- ensemble
- active
---

# Improving Data-Constrained Scaling with Hyperparameter Transfer and Ensembling

## Abstract Summary
Prior data-constrained recipes freeze HPs with scale and ignore ensembling, so loss can rise with compute. Power laws transfer LR/WD/etc with scale, and a second law allocates compute to ensembles. Fit on small runs, hold at up to 12x compute.

## Key Contributions
1. HP-transfer power laws plus ensembling under a unique-token budget.

## Empirical Highlights
FineWeb 100M unique tokens: val loss -0.15 nats vs prior recipes (14% PPL drop); monotonic in compute via ensembling. No public code. Does not retarget method:repeated-token-worth / method:repetition-count-selection.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37842`
- Code: `none found (`code_status: none`).`
