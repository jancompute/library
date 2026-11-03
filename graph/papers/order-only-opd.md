---
id: paper:order-only-opd
type: paper
title: 'Order-Only On-Policy Distillation'
authors:
- 'Guangzeng Han'
- 'Yu Wu'
- 'Xiaolei Huang'
year: 2026
month: 11
arxiv_id: '2611.02112'
url: https://arxiv.org/abs/2611.02112
methods:
- method:order-only-opd
cites:
- paper:opd
tags:
- opd
- ordinal
- active
---

# Order-Only On-Policy Distillation

## Abstract Summary
Teacher probabilities entangle ranking with confidence. Order-Only On-Policy Distillation (O3PD) trains the student to reproduce the order of the teacher's top-K tokens without fitting probability values, so the objective is invariant to teacher temperature. Across six teacher-student pairs it beats OPD on the HMMT25/AIME24/AIME25 average in every pair.

## Key Contributions
1. Ordinal top-K OPD that drops teacher probability values.

## Empirical Highlights
Up to +2.9 average and +5.6 AIME25 vs OPD across six pairs. Other ranking losses yield similar gains, so the benefit is ordinal supervision itself.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02112`
- Code: none found (`code_status: none`).
