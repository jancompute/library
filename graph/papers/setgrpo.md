---
id: paper:setgrpo
type: paper
title: 'SetGRPO: Calibrating Grader-Induced Policy Optimization'
authors:
- 'Jiale Huang'
- 'Zixu Li'
- 'Zhiwei Chen'
- 'Zhiheng Fu'
- 'Jinhe Bi'
- 'Yupeng Hu'
year: 2026
month: 10
arxiv_id: '2610.36807'
url: https://arxiv.org/abs/2610.36807
methods:
- method:setgrpo
cites:
- paper:corrgrpo
tags:
- rlvr
- multi-reward
- active
---

# SetGRPO: Calibrating Grader-Induced Policy Optimization

## Abstract Summary
Grader randomness can shift an entire GRPO group's training coefficients. SetGRPO jointly calibrates a coefficient uncertainty set, recovers a geometry-safe ratio, and risk-gates accepted updates.

## Key Contributions
1. SetGRPO as an active grader-calibration plug-in on task:multi-reward-rlvr.

## Empirical Highlights
Highest macro average among compared methods on ten open-ended benches for Qwen3.5 and Llama3.2. Does not retarget method:corrgrpo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36807`
- Code: `none found (`code_status: none`).`
