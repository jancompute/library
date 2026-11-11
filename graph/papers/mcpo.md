---
id: paper:mcpo
type: paper
title: 'Margin-Guided Token Credit for Reinforcement Learning with Verifiable Rewards'
authors:
- Chi Liu
- Xin Chen
- Yuchuan Weng
- Srinivasan Manoharan
year: 2026
month: 11
arxiv_id: '2611.14015'
url: https://arxiv.org/abs/2611.14015
methods:
- method:mcpo
cites:
- paper:minimax-m1
tags:
- rlvr
- token-credit
- margin
- grpo
- active
---

# Margin-Guided Token Credit for Reinforcement Learning with Verifiable Rewards

## Abstract Summary
MCPO redistributes each GRPO completion's advantage over tokens by the old-policy top-2 margin $M=p_1-p_2$. MiniCPM5-2B-Base macro avg@32 $+6.55$ vs GRPO (95% CI $[4.1,9.0]$); Qwen3-4B-Base $+4.75$. No extra forward pass. No dedicated public trainer as of 2026-11-11.

## Key Contributions
1. Fixed-threshold top-2 margin as a token-credit score; no batch statistics.
2. Mean-preserving reweight of the GRPO advantage (Yeo et al. 2026 host, entropy score off).
3. 16 runs, seed-level CIs, pass@$k$ growing with $k$.

## Empirical Highlights
MiniCPM5-2B $+6.55$ / Qwen3-4B $+4.75$ vs unmodified GRPO on six competition-math benches. Gain largest on intermediate-difficulty prompts; pass@32 $+13.8$. Answers 2–3× longer. Does not retarget CISPO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.14015`
- Code: none found (`code_status: none`).
