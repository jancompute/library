---
id: paper:opd-ood-consolidation
type: paper
title: 'On the Generalization Limitation of On-Policy Distillation for Post-RL Consolidation'
authors:
- Yichen Wang
- Yufa Zhou
- Siqi Zhu
- Haozheng Luo
- Jingzhi Bao
- Zhichao Liu
- Zijun Wei
year: 2026
month: 11
arxiv_id: '2611.05609'
url: https://arxiv.org/abs/2611.05609
methods:
- method:opd
- method:open-mopd
cites:
- paper:opd
- paper:open-mopd
- paper:self-distillation-ood
tags:
- distillation
- ood
- gotcha
---

# On the Generalization Limitation of On-Policy Distillation for Post-RL Consolidation

## Abstract Summary
(M)OPD can look near-perfect in-distribution while leaving OOD capability below the base model. IND scores sit at 96.04–102.73% of teachers; extrapolative OOD stays 2.45–16.25% below base; compositional OOD stays 18.19–24.34% below the best teachers. Complements `paper:self-distillation-ood` / `paper:opd-failure-problems` / `paper:opd-skill-not-knowledge`.

## Key Contributions
1. IND consolidation is not OOD retention for OPD / MOPD after RL.
2. Jointly covering teacher capability and data coverage removes OOD forgetting in the paper's experiments; geometry-based patching and base-preserving replay are proposed, not library methods.

## Empirical Highlights
Gotcha on `task:student-distillation`. Does not retarget OPD or Open-MOPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.05609`
- Code: none found (`code_status: none`).
