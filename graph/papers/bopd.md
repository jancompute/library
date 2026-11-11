---
id: paper:bopd
type: paper
title: 'Bootstrapped On-Policy Distillation'
authors:
- Yue Wu
- Xueyu Zhou
- Yangrong Hu
- Jian Huang
year: 2026
month: 11
arxiv_id: '2611.13680'
url: https://arxiv.org/abs/2611.13680
methods:
- method:bopd
cites:
- paper:opd
- paper:vista
tags:
- distillation
- opsd
- opd
- bootstrap
- active
---

# Bootstrapped On-Policy Distillation

## Abstract Summary
Prolonged OPSD can reverse its early gains because the privileged teacher and the reference-free student diverge. BOPD first internalizes the reference into an intermediate model, then distills that model into a fresh copy of the initial checkpoint without privileged context. Qwen3-4B math mean Avg@12 $18.06\to 23.98$ vs OPSD $19.63$. Code YueWu0301/BOPD released.

## Key Contributions
1. Documents OPSD late-training mismatch (Overlap@16 drop, entropy-gap rise).
2. Two-stage bootstrap: OPSD teacher construction, then reference-free OPD.
3. The Stage II student beats both the initial model and the OPSD teacher on math.

## Empirical Highlights
Qwen3-4B/8B AIME24/25/HMMT25 mean Avg@12 $23.98$ / $22.04$ vs OPSD $19.63$ / $20.19$. SmolLM3-3B mean Avg@12 $13.15$ vs OPSD $12.31$. Does not retarget VISTA.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.13680`
- Code: `https://github.com/YueWu0301/BOPD` (`code_status: released`).
