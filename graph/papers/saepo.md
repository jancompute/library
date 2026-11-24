---
id: paper:saepo
type: paper
title: 'SAEPO: Sparse-Autoencoder-Guided Credit Assignment for Policy Optimization'
authors:
- Yusong Zhao
- Zihao Zhao
- Zirui Zhang
- Tunyu Zhang
- Ziyan Wang
- Yi Wang
- Chengzhi Mao
- Hao Wang
year: 2026
month: 11
arxiv_id: '2611.29936'
url: https://arxiv.org/abs/2611.29936
methods:
- method:saepo
cites: []
tags:
- rlvr
- sae
- credit-assignment
- grpo
---

# SAEPO: Sparse-Autoencoder-Guided Credit Assignment for Policy Optimization

## Abstract Summary
SAEPO reshapes GRPO/GSPO token advantages with a frozen SAE: tokens similar to correct-group tokens get credit, tokens similar to incorrect-group tokens get penalized. Verifier, clip, and KL stay unchanged. SAE is train-only. Distinct from GMTS / CreditFilter / APRM. No public code.

## Key Contributions
1. Question-local SAE feature contrast between correct and incorrect rollouts of the same prompt.
2. Drop-in token advantage for both token-ratio GRPO and sequence-ratio GSPO.
3. Math and code gains on Qwen3-1.7B/4B-Base and OLMo-3-7B-Base vs KTAE / THR / GTPO.

## Empirical Highlights
Qwen3-1.7B-Base GRPO math avg 35.56→38.68; GSPO 36.63→39.55. Qwen3-4B-Base GRPO code avg 12.11→17.68 (+5.57). Abstract ceiling +6.63 math / +5.57 code. Silent groups get no SAE signal.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.29936`
- Code: none found as of 2026-11-24
