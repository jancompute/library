---
id: paper:unsupervised-rlvr-collapse
type: paper
title: 'Collective Dynamics of Self-Reinforcement: How Cross-Task Coupling Drives Policy Collapse in Unsupervised RLVR'
authors:
- 'Peize Ding'
year: 2026
month: 10
arxiv_id: '2610.37553'
url: https://arxiv.org/abs/2610.37553
methods:
- method:u-opsd
cites:
- paper:u-opsd
tags:
- rlvr
- gotcha
- label-free
---

# Collective Dynamics of Self-Reinforcement: How Cross-Task Coupling Drives Policy Collapse in Unsupervised RLVR

## Abstract Summary
Label-free majority-vote RLVR improves then collapses as self-reward goes to one and accuracy falls, but only when many problems are trained together. A shared coupling mode grows independently of N while per-problem sharpening slows as 1/N. Removing the shared direction prevents collapse.

## Key Contributions
1. Unsupervised RLVR collapse gotcha on task:label-free-reasoner-posttrain; not a u-OPSD replacement.

## Empirical Highlights
Collapse grows with training-set size and base-model entropy; a confident init and removing the shared direction prevent it. Does not retarget method:u-opsd.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37553`
- Code: `none found (`code_status: none`).`
