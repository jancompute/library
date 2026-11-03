---
id: paper:proland
type: paper
title: 'ProLand: A New Infeasible Manifold Optimization Method for LoRA Fine-Tuning'
authors:
- 'Chenyu Zhou'
- 'Yuxuan Zeng'
- 'Qi Deng'
- 'Dongdong Ge'
- 'Yinyu Ye'
year: 2026
month: 11
arxiv_id: '2611.00236'
url: https://arxiv.org/abs/2611.00236
methods:
- method:proland
cites:
- paper:lr-matters-lora
- paper:muon2
tags:
- peft
- lora
- active
---

# ProLand: A New Infeasible Manifold Optimization Method for LoRA Fine-Tuning

## Abstract Summary
LoRA can suffer from redundant basis directions. Constraining the basis factor to the Stiefel manifold restores orthonormality. Landing methods allow temporarily infeasible iterates while restoring orthogonality without per-step retractions. ProLand (Product-space Landing) is a retraction-free optimizer that coordinates factor updates with Muon-style spectral directions in the space of the represented weight increment, separating objective optimization from orthogonality restoration.

## Key Contributions
1. Retraction-free Stiefel landing for LoRA with Muon-style spectral directions on the weight increment.

## Empirical Highlights
Highest average among compared methods on four GLUE tasks (DeBERTa-v3-base) and seven decoder benchmarks (Qwen2.5-3B, Llama-3.2-3B, Moonlight-16B-A3B) in every tested encoder and decoder model-rank configuration.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.00236`
- Code: none found (`code_status: none`).
