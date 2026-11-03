---
id: paper:oc-opd
type: paper
title: 'OC-OPD: Observation-coordinated Supervision for On-Policy Distillation'
authors:
- 'Ruoran Xu'
- 'Yilun Zhao'
- 'Ziyu Chen'
- 'Arman Cohan'
year: 2026
month: 11
arxiv_id: '2611.01965'
url: https://arxiv.org/abs/2611.01965
methods:
- method:oc-opd
cites:
- paper:opd
tags:
- opd
- kl
- active
---

# OC-OPD: Observation-coordinated Supervision for On-Policy Distillation

## Abstract Summary
Reverse and forward KL are complementary in OPD. OC-OPD builds a four-observation matrix treating student and teacher as both candidate sources and evaluators, then uses closed-form bargaining and distributional discrepancy to scale the update. An identity equates Fisher inverse-metric coupling of logit gradients with the sum of these contrasts.

## Key Contributions
1. Observation-coordinated OPD with closed-form gradient bargaining across reverse and forward KL.

## Empirical Highlights
Strong math-reasoning gains and OOD transfer to scientific QA and code across non-thinking, thinking, and base-model student settings. Code github.com/RuoranXu/OC-OPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.01965`
- Code: `https://github.com/RuoranXu/OC-OPD` (`code_status: released`).
