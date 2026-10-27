---
id: paper:papo
type: paper
title: 'Priority-Preserving Advantage Aggregation for Multi-Reward Policy Optimization'
authors:
- 'Xiangchi Yuan'
- 'Xingjian Diao'
- 'Zheyuan Liu'
- 'Chunhui Zhang'
- 'Dachuan Shi'
- 'Kejing Xia'
- 'Zhenbang Du'
- 'Shenglong Yao'
- 'Soroush Vosoughi'
- 'Wenke Lee'
year: 2026
month: 10
arxiv_id: '2610.34862'
url: https://arxiv.org/abs/2610.34862
methods:
- method:papo
cites:
- paper:corrgrpo
- paper:dara
tags:
- rlvr
- multi-reward
- active
---

# Priority-Preserving Advantage Aggregation for Multi-Reward Policy Optimization

## Abstract Summary
Additive multi-reward aggregation can invert the primary objective when the auxiliary advantage is large. PAPO keeps auxiliary signal when signs agree and attenuates it when they conflict. Project https://xiangchi-yuan.github.io/papo-project/

## Key Contributions
1. PAPO as an active plug-in on task:multi-reward-rlvr.

## Empirical Highlights
Best primary objective with competitive auxiliary scores on GRPO- and PPO-style hosts. Does not retarget method:corrgrpo or method:dara.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34862`
- Code: `https://xiangchi-yuan.github.io/papo-project/ (`code_status: announced`).`
