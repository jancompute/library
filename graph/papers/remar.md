---
id: paper:remar
type: paper
title: 'ReMaRL: Learning to Unmask and Remask in Frozen Diffusion Language Models'
authors:
- Egor Shibaev
- Danila Biktimirov
- Ivan Klimov
- Artem Makoian
- Viacheslav Meshchaninov
- Dmitry Vetrov
year: 2026
month: 11
arxiv_id: '2611.22576'
url: https://arxiv.org/abs/2611.22576
methods:
- method:remar
cites: []
tags:
- dllm
- remasking
- grpo
- active
---

# ReMaRL: Learning to Unmask and Remask in Frozen Diffusion Language Models

## Abstract Summary
ReMaRL is a ~0.3M-parameter GRPO policy that chooses unmask / retain / remask on a frozen dLLM, starting from stochastic P2′ confidence scores. LLaDA-8B-Instruct GSM8K at NFE8: 53.60 vs P2′ \(\tau=1\) 28.76 (+24.84) and vs temperature-calibrated P2′ \(\tau=0.25\) 42.30 (+11.30). Highest among compared unmask/remask policies at 4–32 math NFEs and 8–16 code NFEs. Code EgorShibaev/remarl. Distinct from TDLM and ForkGRPO. Does not retarget A2D.

## Key Contributions
1. Residual correction of P2′ position scores trained with GRPO from final-answer rewards while the dLLM stays frozen.
2. Stochastic P2′ baseline (current-token scoring plus temperature) as a strong no-train remasker.
3. Data-efficient: four questions per math dataset already beat calibrated P2′ at NFE8.

## Empirical Highlights
LLaDA-8B-Instruct NFE8 GSM8K 53.60 vs P2′ \(\tau=1\) 28.76 / calibrated \(\tau=0.25\) 42.30. NFE16 GSM8K 65.13 vs 56.25 calibrated. HumanEval/MBPP NFE8 20.73 / 25.40 vs calibrated 14.23 / 21.47.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.22576`
- Code: `https://github.com/EgorShibaev/remarl` (`code_status: released`; size 3013 as of 2026-11-18).
