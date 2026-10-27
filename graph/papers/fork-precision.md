---
id: paper:fork-precision
type: paper
title: 'Eat Your Precision: Precision Objective Mitigates Reward Hacking in Rubric-based RL'
authors:
- 'Hyun Ryu'
- 'Jong-Heon Kim'
- 'Yiqing Xie'
- 'Seungone Kim'
- 'Carolyn Rose'
- 'Eunho Yang'
year: 2026
month: 10
arxiv_id: '2610.33512'
url: https://arxiv.org/abs/2610.33512
methods:
- method:fork-precision
cites:
- paper:draco
- paper:canopy
tags:
- rlvr
- rubric
- active
---

# Eat Your Precision: Precision Objective Mitigates Reward Hacking in Rubric-based RL

## Abstract Summary
Rubric rewards that score coverage train recall, so RL answers get longer, noisier, and less preferred. FORK adds a precision objective: each response unit must be necessary and factually correct.

## Key Contributions
1. FORK as an active plug-in on task:outcome-only-long-horizon-agent-rl. Distinct from method:forkgrpo.

## Empirical Highlights
Outperforms coverage-only rubric RL and is Pareto-optimal on completeness vs precision. Does not retarget method:canopy or method:draco.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.33512`
- Code: `none found (`code_status: none`).`
