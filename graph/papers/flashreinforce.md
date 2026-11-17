---
id: paper:flashreinforce
type: paper
title: 'FlashREINFORCE: Critic-Free Single-Rollout Asynchronous RL for Agentic Language Models'
authors:
- Jian Hu
- Yifan Zhang
- Hao Zhang
- Binfeng Xu
- Shaokun Zhang
- Hongqing Peng
- Zhiding Yu
- Pavlo Molchanov
- Jan Kautz
- Yi Dong
year: 2026
month: 11
arxiv_id: '2611.18627'
url: https://arxiv.org/abs/2611.18627
methods:
- method:flashreinforce
cites: []
tags:
- async-rl
- reinforce
- critic-free
- active
---

# FlashREINFORCE: Critic-Free Single-Rollout Asynchronous RL for Agentic Language Models

## Abstract Summary
Critic-free one-pass RL for async agents: One-Batch REINFORCE, Sequence Trust Region, Sample-Mean Optimization. One rollout per prompt. Qwen2.5-Math-1.5B 38.0 mean vs GRPO +1.7 at half rollouts (256k vs 512k). Stable 6,000 updates at lag ~4 on DeepSeek-R1-Distill-Qwen-1.5B. Qwen2.5-7B-Instruct ALFWorld 98.3%/96.5% and keeps tools where GRPO stops calling. Qwen3-30B-A3B Python-tool lag 8. Code in NVIDIA-NeMo/labs-molt. Does not retarget SAO / CISPO.

## Key Contributions
1. One rollout per prompt removes group-sync barriers without a learned critic.
2. Sequence trust region plus sample-mean optimization control drift and length-amplified negatives.
3. Tool-use does not collapse the way GRPO does on ALFWorld in the paper.

## Empirical Highlights
38.0 vs GRPO +1.7 at 256k vs 512k rollouts. ALFWorld 98.3%/96.5%. 6k updates at lag ~4. 30B-A3B lag 8.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.18627`
- Code: `https://github.com/NVIDIA-NeMo/labs-molt` (`code_status: released`; `examples/scripts/quick_start/rl_flash_reinforce_r1d_1p5b.sh`).
