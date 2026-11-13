---
id: paper:lgpo
type: paper
title: 'Is the Importance Ratio Necessary for Stable Reinforcement Learning in LLMs?'
authors:
- Shuibai Zhang
- Junhyuck Kim
- Gyeongman Kim
- Jaewoong Cho
year: 2026
month: 11
arxiv_id: '2611.15404'
url: https://arxiv.org/abs/2611.15404
methods:
- method:lgpo
cites: []
tags:
- rlvr
- grpo
- on-policy
- active
---

# Is the Importance Ratio Necessary for Stable Reinforcement Learning in LLMs?

## Abstract Summary
LGPO replaces the GRPO-style importance ratio with a likelihood gate so fully on-policy updates (ratio $=1$) still have a trust region. Drops the old-policy likelihood pass. Qwen2.5-3B 3.37h→2.85h per epoch (~18% train time). Threshold $\tau$ near the top 10–20% likelihood quantile. No public code. Does not retarget CISPO.

## Key Contributions
1. Ratio clipping is a no-op when the sampler and trainer are the same policy (ratio $=1$).
2. Likelihood gating keeps a soft trust region from current-policy logp only.
3. Skipping old-policy likelihoods cuts train time without a new loss family.

## Empirical Highlights
Qwen2.5-3B 3.37h→2.85h/epoch (~18%). $\tau$ near the top 10–20% quantile. Host is GRPO-family RLVR. No public trainer as of 2026-11-13.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.15404`
- Code: none found (`code_status: none`).
