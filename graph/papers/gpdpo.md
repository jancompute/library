---
id: paper:gpdpo
type: paper
title: 'GPDPO: Learning from Reward Conflicts via Group Pareto-Dominance Policy Optimization'
authors:
- 'Zixuan Xu'
- 'Haoxuan Chen'
- 'Jiangxin Sun'
- 'Jian-Fang Hu'
year: 2026
month: 10
arxiv_id: '2610.35480'
url: https://arxiv.org/abs/2610.35480
methods:
- method:gpdpo
cites:
- paper:corrgrpo
- paper:dara
tags:
- rlvr
- multi-reward
- active
---

# GPDPO: Learning from Reward Conflicts via Group Pareto-Dominance Policy Optimization

## Abstract Summary
Conflict filtering in multi-reward RL discards rollouts that still have pairwise Pareto structure. GPDPO turns those dominance relations into auxiliary preferences and jointly optimizes them with the policy loss.

## Key Contributions
1. GPDPO as an active plug-in on task:multi-reward-rlvr.

## Empirical Highlights
API-Bank: beats multi-reward baselines across scales; lowers group-relative and pairwise conflicts. Does not retarget method:corrgrpo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.35480`
- Code: `none found (`code_status: none`).`
