---
id: paper:not-all-reasoning-generalizes
type: paper
title: 'Not All Reasoning Generalizes: A Case Study on Learning Generalizable Reasoning Strategies in RLVR'
authors:
- 'Ziqi Pang'
- 'Yu-Xiong Wang'
year: 2026
month: 11
arxiv_id: '2611.03627'
url: https://arxiv.org/abs/2611.03627
methods:
- method:cispo
cites:
- paper:minimax-m1
tags:
- rlvr
- gotcha
---

# Not All Reasoning Generalizes: A Case Study on Learning Generalizable Reasoning Strategies in RLVR

## Abstract Summary
On a controllable non-bijective equation-solving task, RLVR learns accurate in-distribution derivation then under OOD (more solutions, longer y) collapses to brute-force enumeration. Co-training on bijective inversion restores the derivation strategy even though those tasks are not uniformly harder.

## Key Contributions
1. ID derivation success is not OOD strategy transfer; bijective co-train restores it.

## Empirical Highlights
Gotcha on task:math-code-rl-dense. Does not retarget CISPO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03627`
- Code: none found (`code_status: none`).
