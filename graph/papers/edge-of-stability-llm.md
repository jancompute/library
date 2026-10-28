---
id: paper:edge-of-stability-llm
type: paper
title: 'Does LLM Pre-Training Typically Occur at the Edge of Stability?'
authors:
- 'Yuhang Cai'
- 'Haodong Wen'
- 'Haofeng Huang'
- 'Deyi Liu'
- 'Yiyuan Ma'
- 'Kaifeng Lyu'
year: 2026
month: 10
arxiv_id: '2610.36778'
url: https://arxiv.org/abs/2610.36778
methods:
- method:muon2
cites:
- paper:muon2
tags:
- optimizer
- gotcha
- stability
---

# Does LLM Pre-Training Typically Occur at the Edge of Stability?

## Abstract Summary
Quadratic approximations fail for LLM training in two ways: Edge of Stability (largest Hessian eigenvalue near 2/eta) and Edge of Convexity, where persistent negative curvature makes the quadratic diverge at any LR while the real dynamics stay stable.

## Key Contributions
1. EoS/EoC claim note on task:llm-pretraining-optimization; not a Muon2 replacement.

## Empirical Highlights
After removing the EoC effect, the remaining EoS picture still does not license a quadratic LR rule for LLM pretrain. Does not retarget method:muon2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36778`
- Code: `none found (`code_status: none`).`
