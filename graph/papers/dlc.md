---
id: paper:dlc
type: paper
title: 'On the Origin and Evolution of Training-Inference Mismatch in LLM Reinforcement Learning'
authors:
- 'Yu Li'
- 'Yufa Zhou'
- 'Tian Lan'
year: 2026
month: 10
arxiv_id: '2610.40945'
url: https://arxiv.org/abs/2610.40945
methods:
- method:dlc
cites:
- paper:trace
- paper:rounding-align-rl
tags:
- rl
- numerics
- active
---

# On the Origin and Evolution of Training-Inference Mismatch in LLM Reinforcement Learning

## Abstract Summary
Disaggregated RL splits sampled-token error into a nearly constant numerical discrepancy of the engine and a policy lag of the trainer. Centering the score at each prefix removes the numerical bias. Importance weighting cuts the lag loop only while the lag ratio stays concentrated; on Qwen3-1.7B it fails when ESS of the ratio falls below one half. Discrepancy-lag correction (DLC) centers the numerical error, clips the lag ratio against the sampler weights, and resynchronizes the sampler when ESS < 0.5.

## Key Contributions
1. Split training-inference mismatch into numerical discrepancy vs policy lag, then DLC.

## Empirical Highlights
Under a stale sampler, DLC keeps KL from on-policy training within 2x the KL between two independent on-policy runs on Qwen3-0.6B and 1.7B. Code github.com/Skylanding/Training-Inference-Mismatch. Does not retarget method:trace.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.40945`
- Code: `https://github.com/Skylanding/Training-Inference-Mismatch` (`code_status: released`).
