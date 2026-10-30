---
id: paper:tesd
type: paper
title: 'On-Policy Self-Distillation with Teacher Evolution'
authors:
- 'Shufan Shen'
- 'Zhongni Hou'
- 'Chao Bi'
- 'Yufei Zhang'
- 'Guojun Yin'
- 'Shuhui Wang'
year: 2026
month: 10
arxiv_id: '2610.38637'
url: https://arxiv.org/abs/2610.38637
methods:
- method:tesd
cites:
- paper:vista
tags:
- opsd
- distillation
- active
---

# On-Policy Self-Distillation with Teacher Evolution

## Abstract Summary
Vanilla OPSD plateaus when the self-teacher is unreliable. TESD lets the self-teacher roll out, scores those traces on task correctness and context independence, uses those rewards to improve the teacher, and down-weights student updates when teacher guidance is unreliable.

## Key Contributions
1. Teacher-evolution loop plus reliability-weighted student OPSD.

## Empirical Highlights
Beats token-level and sequence-level OPSD baselines across scales. No public code. Does not retarget method:vista.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.38637`
- Code: `none found (`code_status: none`).`
