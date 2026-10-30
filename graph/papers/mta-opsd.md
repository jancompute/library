---
id: paper:mta-opsd
type: paper
title: 'Every Token Needs Its Own Teacher: Multi-teacher Adaptive On-policy Self-distillation'
authors:
- 'Yifu Luo'
- 'Chuang Ma'
- 'Zeyu Chen'
- 'Enkelejda Kasneci'
- 'Qi Chen'
- 'Gjergji Kasneci'
year: 2026
month: 10
arxiv_id: '2610.40574'
url: https://arxiv.org/abs/2610.40574
methods:
- method:mta-opsd
cites:
- paper:vista
tags:
- opsd
- multi-teacher
- active
---

# Every Token Needs Its Own Teacher: Multi-teacher Adaptive On-policy Self-distillation

## Abstract Summary
Privileged OPSD usually freezes one teacher (full reference) or varies exposure only across responses. MTA-OPSD picks a teacher per token by majority vote and KL, because preferred privileged context can change inside one response.

## Key Contributions
1. Token-level multi-teacher adaptive privileged OPSD.

## Empirical Highlights
Code github.com/xingzhejun/MTA-OPSD. Does not retarget method:vista.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.40574`
- Code: `https://github.com/xingzhejun/MTA-OPSD (`code_status: released`).`
