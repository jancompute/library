---
id: paper:stage-lora
type: paper
title: 'Spectral and Subspace Dynamics of LoRA in Supervised Fine-Tuning and Reinforcement Learning'
authors:
- Chenruo Liu
- Zihan Wang
- Yijun Dong
- Qi Lei
year: 2026
month: 11
arxiv_id: '2611.08414'
url: https://arxiv.org/abs/2611.08414
methods:
- method:stage-lora
cites:
- paper:lr-matters-lora
- paper:muon2
tags:
- peft
- lora
- active
---

# Spectral and Subspace Dynamics of LoRA in Supervised Fine-Tuning and Reinforcement Learning

## Abstract Summary
LoRA $\Delta W$ under SFT expands the singular spectrum at moderate LRs; GRPO concentrates it at every LR and rotates subspaces faster at small LRs. Group-mean baseline subtraction is the mechanism. Stage-specific updates: SFT flattens the full $B$ update with SGD-style $\mathcal{M}$; RL flattens only the component of the Adam $B$ update orthogonal to the current LoRA span ($\mathcal{M}_\perp$).

## Key Contributions
1. Isolates group-mean baseline subtraction as the SFT vs RL LoRA spectral split.
2. GSM8K Llama-3.2-1B/3B SFT $\mathcal{M}(\mathrm{SGD})$ $22.82$ / $45.72$ vs Adam $22.24$ / $42.99$.
3. Same models RL $\mathcal{M}_\perp(\mathrm{Adam})$ $10.00$ / $47.66$ vs Adam $7.61$ / $42.36$.

## Empirical Highlights
Table 1. No public code as of 2026-11-06. Does not supersede vanilla LoRA + rsLoRA + LR sweep.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.08414`
- Code: none found (`code_status: none`).
