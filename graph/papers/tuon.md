---
id: paper:tuon
type: paper
title: 'TUON: A Tensor-Aware Optimizer Utilizing Tensor-SVD and Polarization for Large Language Model Pretraining'
authors:
- 'Anda Tang'
- 'Xuanlin Yang'
- 'Junjie Wang'
- 'Zhouchen Lin'
year: 2026
month: 10
arxiv_id: '2610.35130'
url: https://arxiv.org/abs/2610.35130
methods:
- method:tuon
cites:
- paper:muon2
- paper:t-muon
tags:
- optimizer
- active
---

# TUON: A Tensor-Aware Optimizer Utilizing Tensor-SVD and Polarization for Large Language Model Pretraining

## Abstract Summary
Muon polarizes each matrix alone. TUON mixes layers with a unitary transform, polarizes each transformed slice, then inverts the mix. Distinct from method:t-muon.

## Key Contributions
1. TUON as an active plug-in on task:llm-pretraining-optimization.

## Empirical Highlights
Steepest descent under a Q-transformed tensor spectral norm; scales past QKV-only stacking. Does not retarget method:muon2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.35130`
- Code: `none found (`code_status: none`).`
