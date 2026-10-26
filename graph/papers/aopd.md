---
id: paper:aopd
type: paper
title: 'When to Follow the Teacher: Advantage-Based On-Policy Distillation'
authors:
- 'Mahdi Sabbaghi'
- 'George Pappas'
- 'Hamed Hassani'
- 'Adel Javanmard'
year: 2026
month: 10
arxiv_id: '2610.31563'
url: https://arxiv.org/abs/2610.31563
methods:
- method:aopd
cites:
- paper:opd
tags:
- distillation
- opd
- active
---

# When to Follow the Teacher

## Abstract Summary
Standard on-policy distillation follows the teacher at every student state. AOPD gates that matching by whether teacher guidance actually helps the student.

## Key Contributions
1. AOPD as an active plug-in on task:student-distillation.

## Empirical Highlights
- Advantage-gated teacher follow vs always-match OPD. Does not retarget method:opd.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.31563`
- Code: `none found` (`code_status: none`).
