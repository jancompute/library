---
id: paper:sparse-teacher-support
type: paper
title: 'Effective Teacher Support for Reasoning Distillation'
authors:
- Lavinia Ghita
- Dhruv Desai
year: 2026
month: 11
arxiv_id: '2611.14850'
url: https://arxiv.org/abs/2611.14850
methods:
- method:sparse-teacher-support
cites: []
tags:
- distillation
- forward-kl
- sparse-vocab
- active
---

# Effective Teacher Support for Reasoning Distillation

## Abstract Summary
NVIDIA. Forward-KL distillation from the teacher's highest-probability vocabulary fraction, renormalized as support is swept from 100% to 0.01%. Qwen3 4B→1.7B: 0.01% vocab ($k=15$ of 151936) with no MMLU-Pro drop; 38% step-time cut when teacher scores are cached; 24% peak memory with a compact student output. Nemotron Nano matches at 0.1%; smaller fractions fail the closing reasoning tag. Distinct from reverse-KL sparse OPD token budgets. No public code. Does not retarget OPD.

## Key Contributions
1. Keep only the teacher's top-mass vocab slice and renormalize; dense full-vocab teacher scores are not required.
2. Cached teacher scores plus a compact student output cut step time and peak memory.
3. Closing reasoning tags fail before MMLU-Pro when support is too small (Nemotron Nano below 0.1%).

## Empirical Highlights
Qwen3 4B→1.7B: 0.01% vocab ($k=15/151936$) no MMLU-Pro drop; 38% step-time cut with cached teacher scores; 24% peak mem. Nemotron Nano matches at 0.1%. Distinct from `method:sparse-opd-supervision` (reverse-KL keep-mask) and `method:order-only-opd` (ordinal top-K without probabilities).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.14850`
- Code: none found (`code_status: none`).
