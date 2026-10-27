---
id: paper:doublefree
type: paper
title: 'DoubleFree: Exploiting Exploration History for Rollout-Free Multi-Task LLMs Training'
authors:
- 'Yingping Wang'
- 'Min Cai'
- 'Chenyu Yuan'
- 'Xi Ye'
- 'Zhijiang Guo'
- 'Jiayi Huang'
year: 2026
month: 10
arxiv_id: '2610.34272'
url: https://arxiv.org/abs/2610.34272
methods:
- method:doublefree
cites:
- paper:open-mopd
- paper:opd
tags:
- distillation
- mopd
- active
---

# DoubleFree: Exploiting Exploration History for Rollout-Free Multi-Task LLMs Training

## Abstract Summary
Domain RL then multi-teacher OPD usually keeps teachers online and samples student rollouts. DoubleFree reuses historical RL trajectories and precomputes teacher supervision so consolidation needs neither live rollouts nor live teachers.

## Key Contributions
1. DoubleFree as an active plug-in on task:student-distillation.

## Empirical Highlights
Rollout-free / teacher-offline consolidation of domain specialists. Does not retarget method:opd or method:open-mopd.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34272`
- Code: `none found (`code_status: none`).`
