---
id: paper:scalerlt
type: paper
title: 'ScaleRLT: Exact Log-Probabilities and Fast Deferred Rollouts for Reinforcement Learning on Looped Transformers'
authors:
- 'Dezhen Lu'
- 'Zixiang Ni'
- 'Runguo Li'
year: 2026
month: 10
arxiv_id: '2610.34427'
url: https://arxiv.org/abs/2610.34427
methods:
- method:scalerlt
cites:
- paper:recurrent-looped-transformer
- paper:looped-models-done-right
tags:
- looped-lm
- rlvr
- active
---

# ScaleRLT: Exact Log-Probabilities and Fast Deferred Rollouts for Reinforcement Learning on Looped Transformers

## Abstract Summary
Deferred looped-transformer rollouts are fast but disagree in float with a dense learner logp (18% of tokens miss 1e-5 in FP32 at 4096; almost all in bf16). ScaleRLT uses a hybrid learner logp whose value is a no-grad replay of the rollout schedule and whose gradient is dense.

## Key Contributions
1. ScaleRLT as an active plug-in on task:recurrent-encoder-decoder-lm.

## Empirical Highlights
Bit-exact replay in 167 FP32 and 28 bf16 cells. One-GPU deferral 1.47-1.56x rollout throughput. GRPO loss vs float64 3.1e-4. Does not retarget method:recurrent-looped-transformer.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34427`
- Code: `none found (`code_status: none`).`
