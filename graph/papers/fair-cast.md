---
id: paper:fair-cast
type: paper
title: 'bf16 Rounding Silently Discards Most RL Policy Updates: A Hidden Training-Inference Mismatch and an Unbiased One-Line Fix'
authors:
- 'Andrew Gao'
- 'William Gao'
year: 2026
month: 10
arxiv_id: '2610.41073'
url: https://arxiv.org/abs/2610.41073
methods:
- method:fair-cast
cites:
- paper:rounding-align-rl
- paper:weight-update-leverage
tags:
- rl
- numerics
- bf16
- active
---

# bf16 Rounding Silently Discards Most RL Policy Updates

## Abstract Summary
RL keeps fp32 master weights and serves rollouts from a bf16 copy via round-to-nearest. At common LRs most per-step updates are smaller than half a bf16 spacing, so the served policy lags 50-150 steps; on Qwen3-1.7B only 0.4-0.5% of served weights change per step. Fair Cast exports with an unbiased rule (stochastic rounding or error feedback) and trains on the served copy. One line at the export call; 22-38 ms per 1.7B export.

## Key Contributions
1. Unbiased fp32 to bf16 export plus train-on-served-copy so RL updates are not silently dropped.

## Empirical Highlights
18/25 matched seed-pairs ahead, 6 tied, 1 behind; mean +6.1. Zebra puzzles 0.57 +/- 0.16 vs round-to-nearest 0.33 +/- 0.10. Code github.com/andrewgcodes/faircast. Distinct from method:rounding-align-rl (rounding location) and method:trace (NVFP4).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.41073`
- Code: `https://github.com/andrewgcodes/faircast` (`code_status: released`).
