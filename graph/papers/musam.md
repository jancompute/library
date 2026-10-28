---
id: paper:musam
type: paper
title: 'Sharpness-Aware Muon: Matrix-Aware Optimization with Momentum-Guided Perturbations'
authors:
- 'Zhiwei Zhai'
- 'Wenjing Yan'
- 'Ying-Jun Angela Zhang'
year: 2026
month: 10
arxiv_id: '2610.37225'
url: https://arxiv.org/abs/2610.37225
methods:
- method:musam
cites:
- paper:muon2
tags:
- optimizer
- muon
- sam
- active
---

# Sharpness-Aware Muon: Matrix-Aware Optimization with Momentum-Guided Perturbations

## Abstract Summary
Muon shapes update geometry but does not control neighborhood worst-case loss. MuSAM injects SAM perturbations into orthogonalized Muon updates. MoMuSAM uses normalized momentum as the perturbation so the extra clean gradient is not required.

## Key Contributions
1. MuSAM / MoMuSAM as an active sharpness-aware Muon plug-in on task:llm-pretraining-optimization.

## Empirical Highlights
Sharpness awareness consistently improves Muon on the paper benches. Does not retarget method:muon2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37225`
- Code: `none found (`code_status: none`).`
