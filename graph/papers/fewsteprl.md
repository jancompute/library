---
id: paper:fewsteprl
type: paper
title: 'FewStepRL: Fine-tuning Few-step Diffusion Models with Reinforcement Learning'
authors:
- Haitao Lin
- Minsi Ren
- Yang Li
- Xingtong Ge
- Zheyuan Hu
- Peiyan Hu
- Tailin Wu
year: 2026
month: 11
arxiv_id: '2611.08240'
url: https://arxiv.org/abs/2611.08240
methods:
- method:fewsteprl
cites:
- paper:diffusion-opsd
tags:
- diffusion
- rl
- few-step
- average-velocity
- active
---

# FewStepRL

## Abstract Summary
FewStepRL adapts FlowGRPO / AWM / DiffusionNFT / DiffusionOPSD / ReFL to few-step average-velocity diffusion models. HF Daily leftover below watermark 2611.09634, ingested 2026-11-10. No public code as of 2026-11-10. Does not replace DiffusionOPSD or Self-OPD.

## Key Contributions
1. Port existing diffusion-RL trainers onto average-velocity few-step models.
2. Keep the host algorithm; change the sampler / velocity parameterization.

## Empirical Highlights
Paper protocol is few-step average-velocity, not the library DiffusionOPSD bake-off. Does not retarget DiffusionOPSD / Self-OPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.08240`
- Code: none found (`code_status: none`).
