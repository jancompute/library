---
id: paper:tide
type: paper
title: 'TIDE: Reclaiming Lost Performance In On-Policy Reinforcement Learning'
authors:
- Mathew Jacob
- Morgan Borjigin-Wang
- Kan Zhu
- Po Hao Chen
- Yi Pan
- Andy Ruan
- Nayani Modugula
- Ethan Lavi
- Luis Ceze
- Malte Schwarzkopf
- Akshay Narayan
- Deepti Raghavan
- Stephanie Wang
year: 2026
month: 11
arxiv_id: '2611.17924'
url: https://arxiv.org/abs/2611.17924
methods:
- method:tide
cites: []
tags:
- rl-systems
- on-policy
- colocated
- active
---

# TIDE: Reclaiming Lost Performance In On-Policy Reinforcement Learning

## Abstract Summary
TIDE reclaims finished colocated rollout GPUs for training and migrates remaining rollouts. Barrier only before the weight update. Up to 1.36× vs colocated; 77–97% of optimal; baseline idle up to 30% plus inefficient decode 9.8%. DAPO-Math / Text2SQL; 4× L40S to 8× H200; Megatron DP+TP and FSDP ZeRO. Distinct from ThunderSyncRL. No dedicated repo. Does not retarget Miles / SAO.

## Key Contributions
1. Colocated on-policy GPU reclaim without going off-policy.
2. Migrate leftover rollouts; barrier only before the weight update.
3. Quantifies idle (up to 30%) and inefficient decode (9.8%) in colocated baselines.

## Empirical Highlights
Up to 1.36× vs colocated. 77–97% of optimal. 4× L40S to 8× H200. DAPO-Math / Text2SQL.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.17924`
- Code: none found (`code_status: none`). Mentions THUDM/slime and ServingStudio. SyFI-ServingStudio/TIDE 404.
