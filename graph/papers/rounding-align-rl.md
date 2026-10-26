---
id: paper:rounding-align-rl
type: paper
title: 'Where Rounding Happens Matters: Rounding-Location Alignment Stabilizes LLM Reinforcement Learning'
authors:
- 'Yijing Ke'
- 'Tianle Cai'
- 'Ruosong Wang'
year: 2026
month: 10
arxiv_id: '2610.32951'
url: https://arxiv.org/abs/2610.32951
methods:
- method:rounding-align-rl
cites:
- paper:trace
tags:
- rl
- numerics
- active
---

# Where Rounding Happens Matters

## Abstract Summary
Split inference/train RL can go off-policy from rounding-site mismatch even in BF16. Aligning where rounding happens stabilizes training.

## Key Contributions
1. Rounding-align RL as an active plug-in on task:fp4-rl-train-rollout-alignment.

## Empirical Highlights
- Rounding-site alignment vs full-stack match. Does not retarget method:trace / method:triage.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.32951`
- Code: `none found` (`code_status: none`).
