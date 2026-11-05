---
id: paper:moe-expert-deactivation-weight-rule
type: paper
title: 'Matching the Training-Time Weight Rule in Inference-Time Expert Deactivation'
authors:
- Hao Cheng
- Zhiyu Yang
- Bo Ma
- Hanzhang Jia
year: 2026
month: 11
arxiv_id: '2611.05804'
url: https://arxiv.org/abs/2611.05804
methods:
- method:deepseek-v4
cites:
- paper:deepseek-v4
- paper:kimi-k3
tags:
- moe
- inference
- gotcha
---

# Matching the Training-Time Weight Rule in Inference-Time Expert Deactivation

## Abstract Summary
Inference-time expert deactivation must reuse the train-time weight rule (raw vs renormalized router weights). Matched deactivation keeps perplexity 1.4–73× intact; a mismatched rule reaches 14–28,740×. DeepSeek-V2-Lite freeze vs renormalize is the extreme cell. GSM8K strict-match on OLMoE falls to zero under all four implementations. Not a train-kernel change.

## Key Contributions
1. Weight-sum model tying deactivation PPL to the train-time routing rule.
2. Removal / freeze / remaining-expert renormalization / unnormalized re-routing compared on identical disabled sets.

## Empirical Highlights
Gotcha on `task:pretrain-moe-frontier`. Does not retarget DeepSeek-V4 / Kimi-K3.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.05804`
- Code: none found (`code_status: none`).
