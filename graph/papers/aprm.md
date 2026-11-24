---
id: paper:aprm
type: paper
title: 'From Rewarding What Models Say to How They Think: Attention Process Reward Model for LLM Reinforcement Learning'
authors:
- Kairong Han
- Nuanqiao Shan
- Ziyu Zhao
- Xinpeng Dong
- Zijing Hu
- Dian Jin
- Leyan Deng
- Junjian Ye
- Lujia Pan
- Fei Wu
- Kun Kuang
year: 2026
month: 11
arxiv_id: '2611.30627'
url: https://arxiv.org/abs/2611.30627
methods:
- method:aprm
cites: []
tags:
- rlvr
- process-reward
- attention
- credit-assignment
---

# From Rewarding What Models Say to How They Think: Attention Process Reward Model for LLM Reinforcement Learning

## Abstract Summary
APRM is a ~46M-parameter process reward on hidden states and attention maps, trained with ranking plus counterfactual attention shuffle. It reshapes GRPO/GPG/DAPO advantages and is refreshed during RL. Distinct from textual PRMs and TIPS. No public code.

## Key Contributions
1. Attention-fused concept pooler plus edge-biased GAT scores internal reasoning, not CoT text.
2. Counterfactual loss makes ranking drop under attention shuffle (78.55%→62.54% at 1.7B).
3. Plug-in on GRPO / GPG / DAPO with an average pass@8 gain of 2.88%.

## Empirical Highlights
Qwen3-1.7B-Base GRPO pass@8 52.62→55.97; GPG+APRM 58.13. Qwen3-4B-Base GRPO 61.68→65.06; GPG+APRM avg@8 47.02 / pass@8 65.84. DAPO+APRM math +1.34 / +4.78; code +1.64 / +2.96. GPG 4B median length −17.08%.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.30627`
- Code: none found as of 2026-11-24
