---
id: paper:bf16-sr
type: paper
title: 'Closing the BF16–FP16 Convergence Speed Gap in RL Post-Training with Stochastic Rounding'
authors:
- Mahdi Nazemi
- Oleg Rybakov
- Tijmen Blankevoort
- Asit Mishra
- Carlo del Mundo
year: 2026
month: 11
arxiv_id: '2611.13545'
url: https://arxiv.org/abs/2611.13545
methods:
- method:bf16-sr
cites:
- paper:fair-cast
tags:
- systems
- bf16
- stochastic-rounding
- rlvr
- active
---

# Closing the BF16–FP16 Convergence Speed Gap in RL Post-Training with Stochastic Rounding

## Abstract Summary
NVIDIA. At typical RLVR learning rates, mixed-precision BF16 converges more slowly than FP16 because round-to-nearest leaves BF16 weights stuck while the FP32 shadow moves. Stochastic rounding on the FP32→BF16 write matches FP16's reward trajectory with less KL drift than raising the BF16 LR, and needs no FP16 loss scaling. No public standalone trainer as of 2026-11-11.

## Key Contributions
1. Weight sticking as the BF16–FP16 RLVR gap, even with bit-exact train/rollout logp.
2. SR on the shadow→BF16 write; forward-pass SR is sufficient.
3. Higher BF16 LR recovers speed but increases KL vs the reference.

## Empirical Highlights
DeepSeek-R1-Distill-Qwen-1.5B/14B and Qwen3-30B-A3B on MATH-1460 / DAPO-Math-17k: BF16+SR reward trajectories overlap FP16. Does not retarget Fair Cast, TRACE/TRIAGE, or Muon2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.13545`
- Code: none found (`code_status: none`).
