---
id: paper:p2-mopd
type: paper
title: 'P2-MOPD: Parameter-Prior Multi-Teacher On-Policy Distillation'
authors:
- Sinuo Wang
- Jiacheng Lu
- Zeyu Zhang
- Maojia Song
- Rui Sun
- Beidi Luan
- Yutong Xie
- Jing Li
- Daxin Jiang
- Qi Wu
- Zuo Bai
year: 2026
month: 11
arxiv_id: '2611.03953'
url: https://arxiv.org/abs/2611.03953
methods:
- method:p2-mopd
cites:
- paper:open-mopd
- paper:opd
tags:
- distillation
- mopd
- active
---

# P2-MOPD: Parameter-Prior Multi-Teacher On-Policy Distillation

## Abstract Summary
P²-MOPD treats domain experts as trainable mixing coefficients over student weights under the same on-policy distillation objective, rather than freezing a linear span of student and expert parameters (task arithmetic). The student stays trainable, so experts act as parameter priors. At $1.7$B, average recovery is $94.7\%$ vs MOPD $80.9\%$. GitHub `SinuoWang/P2-MOPD` is README-only as of 2026-11-09 (`code_status: announced`). Paper Open-MOPD numbers are not the library $83.4\%$ bake-off.

## Key Contributions
1. Joint optimization of mixing coefficients and student weights under live OPD.
2. Experts as parameter priors without confining the student to the frozen merge span.
3. Faster balanced recovery: surpasses MOPD final average recovery in half the steps; worst-domain recovery from below $50\%$ to about $90\%$.

## Empirical Highlights
Four domains at $1.7$B / $4$B: average recovery $94.7\%$ / $94.9\%$ vs MOPD $80.9\%$ / $\approx 86\%$. Does not retarget Open-MOPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03953`
- Code: `https://github.com/SinuoWang/P2-MOPD` (`code_status: announced`; README-only as of 2026-11-09).
