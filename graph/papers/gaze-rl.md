---
id: paper:gaze-rl
type: paper
title: 'Eyes in the Update? Learning Where Rewards Land in Multimodal Reasoning'
authors:
- Lixuan He
- Tianzhe Chu
- Shulin Tian
- Shikang Zheng
- Feng Chen
- Yi Ma
year: 2026
month: 11
arxiv_id: '2611.22438'
url: https://arxiv.org/abs/2611.22438
methods:
- method:gaze-rl
cites: []
tags:
- multimodal-rl
- credit-assignment
- vision
- active
---

# Eyes in the Update? Learning Where Rewards Land in Multimodal Reasoning

## Abstract Summary
Gaze-RL redistributes a completion-level advantage through a mean-one latent reward landing field from internal cross-modal geometry and predictive entropy. No process labels, extra perception head, or architecture change. Qwen2.5-VL-7B Geometry3K 36.8→47.9 vs GRPO 39.6 / DAPO 41.9; MathVista 67.2→70.4 vs GRPO 68.6. Code lixuan27/Gaze-RL-main. Distinct from Vision-RL2, CycleGRPO, EPS, OraRL. Does not retarget Vision-RL2.

## Key Contributions
1. Mean-one reward landing field \(\varphi_t\) from visual support and local entropy.
2. Token advantage \(\widetilde{A}_t=((1-\gamma)+\gamma\varphi_t)\widehat{A}\) keeps rollout credit, changes only allocation.
3. Same 200-update budget vs GRPO / DAPO / VPPO on Qwen2.5-VL-3B/7B and InternVL3.5-8B.

## Empirical Highlights
Qwen2.5-VL-7B Geometry3K 47.9 vs GRPO 39.6 / DAPO 41.9 / VPPO 44.0; MathVista 70.4 vs GRPO 68.6. InternVL3.5-8B Geometry3K 48.1 vs GRPO 43.2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.22438`
- Code: `https://github.com/lixuan27/Gaze-RL-main` (`code_status: released`; size 829 as of 2026-11-18).
