---
id: paper:ati-opd
type: paper
title: 'ATI-OPD: Adaptive Teacher Intervention for Stable Long-Sequence On-Policy Distillation'
authors:
- 'Jiannan Guan'
- 'Youxin Jiang'
- 'Yutai Hou'
- 'Qiguang Chen'
- 'Yirong Zeng'
- 'Haitao Wang'
- 'Dengyun Peng'
- 'Zheng Yan'
- 'Jinhao Liu'
- 'Tao Ye'
- 'Dandan Tu'
- 'Wanxiang Che'
year: 2026
month: 10
arxiv_id: '2610.38160'
url: https://arxiv.org/abs/2610.38160
methods:
- method:ati-opd
cites:
- paper:opd
tags:
- distillation
- opd
- active
---

# ATI-OPD: Adaptive Teacher Intervention for Stable Long-Sequence On-Policy Distillation

## Abstract Summary
Long student prefixes can leave the teacher's reasoning, so later teacher logp becomes off-target and OPD destabilizes. ATI-OPD replaces the earliest high-disagreement segment with a short teacher segment, then lets the student resume; it repeats if disagreement returns, instead of discarding late reasoning with a fixed cutoff.

## Key Contributions
1. Adaptive teacher-prefix intervention for long-sequence OPD.

## Empirical Highlights
Stabilizes long-CoT OPD vs length control / loss reweighting. No public code. Does not retarget method:opd.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.38160`
- Code: `none found (`code_status: none`).`
