---
id: paper:adaroll-grpo
type: paper
title: 'Bayes-Adaptive MDPs for Rollout Allocation to Enhance GRPO Training'
authors:
- 'Faeze Moradi Kalarde'
- 'Armin Toroghi'
- 'Nam Ho Koh'
- 'Doo Hwan Hwang'
- 'Seungjin Kim'
- 'Kee-Eung Kim'
- 'Scott Sanner'
year: 2026
month: 10
arxiv_id: '2610.37429'
url: https://arxiv.org/abs/2610.37429
methods:
- method:adaroll-grpo
cites:
- paper:minimax-m1
- paper:ngu
tags:
- rlvr
- allocation
- active
---

# Bayes-Adaptive MDPs for Rollout Allocation to Enhance GRPO Training

## Abstract Summary
Uniform GRPO rollout counts ignore difficulty. AdaRoll-GRPO learns an offline BAMDP allocation policy and applies it at train time with no extra online optimizer.

## Key Contributions
1. AdaRoll-GRPO as an active rollout-allocation plug-in on task:math-code-rl-dense.

## Empirical Highlights
Improves GRPO under a matched total rollout budget across reasoning datasets and architectures. Does not retarget method:cispo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37429`
- Code: `none found (`code_status: none`).`
