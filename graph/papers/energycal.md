---
id: paper:energycal
type: paper
title: 'EnergyCal: Taming Loss Spikes in Muon-Family Optimizers for Sparse MoE Training'
authors:
- 'Masato Fujitake'
year: 2026
month: 10
arxiv_id: '2610.37062'
url: https://arxiv.org/abs/2610.37062
methods:
- method:energycal
cites:
- paper:muon2
tags:
- optimizer
- muon
- moe
- active
---

# EnergyCal: Taming Loss Spikes in Muon-Family Optimizers for Sparse MoE Training

## Abstract Summary
Sparse MoE LM training can spike under Muon-family optimizers. EnergyCal attenuates routed-expert updates from the normalized squared Frobenius norm of finite-step Newton-Schulz directions, with no extra optimizer state.

## Key Contributions
1. EnergyCal as an active Muon-MoE spike plug-in on task:llm-pretraining-optimization.

## Empirical Highlights
On a 4B MoE, EnergyCal-MuonH reduces mean thresholded spike burden 99.51% and geomean PPL 4.06% vs a lower-LR MuonH recipe. Does not retarget method:muon2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37062`
- Code: `none found (`code_status: none`).`
