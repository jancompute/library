---
id: paper:moeresq
type: paper
title: 'MoeResQ: Residual-Corrected FP4 RL for Mixture-of-Experts'
authors:
- 'Hei Yi Mak'
- 'Hoang Le'
- 'Mehran Taghian Jazi'
- 'Yunke Peng'
- 'Huan Lin'
- 'Zhengzhi Tang'
- 'Zhexu Liu'
- 'Yao Wang'
- 'Yaoyuan Wang'
- 'Anandharaju Durai Raju'
- 'Tanzila Rahman'
year: 2026
month: 11
arxiv_id: '2611.04376'
url: https://arxiv.org/abs/2611.04376
methods:
- method:moeresq
cites:
- paper:trace
- paper:triage
- paper:sapo
tags:
- quantization
- fp4
- rl-alignment
- moe
- active
---

# MoeResQ: Residual-Corrected FP4 RL for Mixture-of-Experts

## Abstract Summary
FP4 RL on MoE LMs collapses when only the rollout engine is quantized. MoeResQ applies a symmetric residual correction on both the trainer and the rollout sampler so the quantized expert path stays close to BF16. Routers stay BF16 (0.041% of params). Simulated HiF4; VeRL + vLLM + FSDP.

## Key Contributions
1. Symmetric residual correction on train and rollout for FP4 MoE RL.
2. Experts-only FP4 with BF16 routers nearly matches full BF16 GRPO.

## Empirical Highlights
Qwen3-30B-A3B GRPO on DAPO-Math: BF16 AMC23 85.10 vs HiF4 65.23 vs RolloutResQ 62.34 vs MoeResQ 84.45. Experts-only: AMC23 84.61 / AIME24 46.98 / AIME25 32.92 / MATH500 86.17.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.04376`
- Code: none found (`code_status: none`).
