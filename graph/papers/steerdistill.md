---
id: paper:steerdistill
type: paper
title: 'SteerDistill: Quantizing LLM Agents via Closed-Loop Teacher Steering'
authors:
- Genming Cui
- Xiangyu Li
- Zixu Hao
- Xin Ding
- Yunxin Liu
- Ting Cao
year: 2026
month: 11
arxiv_id: '2611.13410'
url: https://arxiv.org/abs/2611.13410
methods:
- method:steerdistill
cites: []
tags:
- quantization
- qat
- agents
- distillation
- active
---

# SteerDistill: Quantizing LLM Agents via Closed-Loop Teacher Steering

## Abstract Summary
Low-bit quantized agents miss task requirements and diverge from full-precision environment transitions. SteerDistill has a BF16 teacher steer failed student turns in a closed loop, then distills locally verified corrections. Across five agentic benches and three models, W4A16 beats the strongest quantized baseline by $1.67$–$2.18$ and stays within $1$ of BF16. Code air-embodied-brain/SteerDistill released.

## Key Contributions
1. Closed-loop teacher steering at the first environment-transition divergence.
2. Internalization: steered-student targets at corrected turns, BF16 teacher elsewhere; no guidance at inference.
3. $\tau^2$-Bench vs QeRL $+1.84$ pp at $67\%$ fewer training GPU hours.

## Empirical Highlights
W4A16 within $1$ of BF16; W2A16 Qwen3-8B margin grows to $3.39$. Unguided retries $9.6\%$ turn-level Pass@4 vs steering $82.3\%$. Successful trajectories $4.0$K output tokens vs BF16 $3.9$K. Does not retarget GradCodeS.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.13410`
- Code: `https://github.com/air-embodied-brain/SteerDistill` (`code_status: released`).
- Project: `https://air-embodied-brain.github.io/SteerDistill`
