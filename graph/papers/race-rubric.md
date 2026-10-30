---
id: paper:race-rubric
type: paper
title: 'Reward-Adaptive Co-Evolution of Policy and Rubric'
authors:
- 'Yizhu Chen'
- 'Jianguang Jiang'
- 'Jiameng Huang'
- 'Chuyu Fang'
- 'Bojun Zhang'
- 'Zhenyu Jiao'
- 'Xing Yuan'
- 'Tong Lin'
year: 2026
month: 10
arxiv_id: '2610.40096'
url: https://arxiv.org/abs/2610.40096
methods:
- method:race-rubric
cites:
- paper:draco
tags:
- rubric
- rl
- active
---

# Reward-Adaptive Co-Evolution of Policy and Rubric

## Abstract Summary
RACE classifies rollout groups as informative, diversity-collapsed, or rubric-failed. Only informative groups update the policy; rubric failures are cached. Persistent reward saturation triggers a rubric-optimization phase that returns when rubric-reward improvement plateaus.

## Key Contributions
1. Reward-adaptive group routing plus event-triggered rubric phases, distinct from CoCA.

## Empirical Highlights
Ignores globally prescribed rubric-update schedules. No public code. Does not retarget method:canopy, method:draco, or method:coca.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.40096`
- Code: `none found (`code_status: none`). Distinct from method:coca.`
