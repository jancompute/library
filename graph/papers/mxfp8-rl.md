---
id: paper:mxfp8-rl
type: paper
title: 'End-to-End MXFP8 Reinforcement Learning on Blackwell: What Matching Buys, When It Pays Off, and How It Fails'
authors:
- 'Wengee Zhang'
year: 2026
month: 10
arxiv_id: '2610.34915'
url: https://arxiv.org/abs/2610.34915
methods:
- method:mxfp8-rl
cites:
- paper:trace
- paper:triage
- paper:minite
tags:
- quantization
- rlvr
- active
---

# End-to-End MXFP8 Reinforcement Learning on Blackwell: What Matching Buys, When It Pays Off, and How It Fails

## Abstract Summary
MXFP8 RL in verl on B200. For an MXFP8 learner, a sampler on the same grid is more consistent than BF16: train-rollout KL -11% with half the sampler linears on-grid and -16% with all of them. Byte-equal synchronized weights.

## Key Contributions
1. MXFP8 matching as an active plug-in on task:fp4-rl-train-rollout-alignment.

## Empirical Highlights
Qwen3-8B and Qwen3-30B-A3B on B200. Off-grid FP8 sampler doubles shared-grid KL on MoE. Implemented in verl; no dedicated repo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34915`
- Code: `none found (`code_status: none`). Host stack: verl.`
