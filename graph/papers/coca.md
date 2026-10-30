---
id: paper:coca
type: paper
title: 'Co-Evolving Policy and Rubric via Capability Awareness for Open-Ended Generation'
authors:
- 'Chengsheng Zhang'
- 'Wenshen Xu'
- 'Yuchuan Wu'
- 'Zhiyuan Yu'
- 'Junfeng Fang'
- 'Tianlong Wang'
- 'Bingxue Qiu'
- 'Yongbin Li'
- 'Xiang Wang'
year: 2026
month: 10
arxiv_id: '2610.38566'
url: https://arxiv.org/abs/2610.38566
methods:
- method:coca
cites:
- paper:draco
tags:
- rubric
- rl
- active
---

# Co-Evolving Policy and Rubric via Capability Awareness for Open-Ended Generation

## Abstract Summary
CoCA diagnoses each rubric criterion by contrasting query-only vs rubric-guided rollouts, recalibrates criteria whose difficulty does not match the current policy, and either expands rubric-conditioned frontiers or retargets the rubric.

## Key Contributions
1. Capability-aware closed-loop policy+rubric co-evolution, distinct from RACE.

## Empirical Highlights
Criterion-level diagnosis vs static or globally scheduled rubric updates. No public code. Does not retarget method:canopy or method:draco.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.38566`
- Code: `none found (`code_status: none`). Distinct from method:race-rubric.`
