---
id: paper:mass-opsd
type: paper
title: 'MASS: Multi-mask Selective Self-Distillation for Leakage-Resilient Reasoning'
authors:
- 'Xiuqi Liu'
- 'Oveys Delafrooz Noroozi'
- 'Upamanyu Madhow'
year: 2026
month: 10
arxiv_id: '2610.38154'
url: https://arxiv.org/abs/2610.38154
methods:
- method:mass-opsd
cites:
- paper:vista
tags:
- opsd
- active
---

# MASS: Multi-mask Selective Self-Distillation for Leakage-Resilient Reasoning

## Abstract Summary
A single privileged reference can lock the teacher onto one trajectory. MASS approximates the missing marginal over references with independently masked views of one verified solution, aggregates those teacher predictions, and transfers only reliable token corrections, focusing masks on influential spans.

## Key Contributions
1. Multi-mask privileged OPSD against single-reference leakage.

## Empirical Highlights
Outperforms strong self-distillation baselines on math reasoning. No public code. Does not retarget method:vista.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.38154`
- Code: `none found (`code_status: none`).`
