---
id: paper:reverse-kl-limits
type: paper
title: 'Reverse-KL Policy Distillation: Statistical Guarantees and Limits'
authors:
- 'Haolin Liu'
- 'Chen-Yu Wei'
- 'Julian Zimmert'
year: 2026
month: 10
arxiv_id: '2610.30844'
url: https://arxiv.org/abs/2610.30844
methods:
- method:opd
cites:
- paper:opd
tags:
- distillation
- gotcha
- opd
---

# Reverse-KL Policy Distillation

## Abstract Summary
Reverse-KL distillation has guarantees, but two design choices matter: full teacher action distribution vs sampled-action logp, and whether training trajectories must cover the student.

## Key Contributions
1. Statistical limits of reverse-KL OPD; not a new matching default.

## Empirical Highlights
- Does not retarget OPD. Full teacher distribution is not automatically a free lunch.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.30844`
- Code: `none found` (`code_status: none`).
