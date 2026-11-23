---
id: paper:creditfilter
type: paper
title: 'CreditFilter: Calibrated Token Weights over the Within-Response Entropy Rank for RLVR'
authors:
- Hanqing Zhao
- Liuyue Xie
- Rong-Cheng Tu
- Xu Zhang
- Davide Modolo
- Dacheng Tao
year: 2026
month: 11
arxiv_id: '2611.27227'
url: https://arxiv.org/abs/2611.27227
methods:
- method:creditfilter
cites: []
tags:
- rlvr
- token-credit
- dapo
- entropy
---

# CreditFilter: Calibrated Token Weights over the Within-Response Entropy Rank for RLVR

## Abstract Summary
CreditFilter weights tokens by an exponential window over within-response entropy rank, with widths from a measured fork-probability envelope, plus difficulty damping. Host is DAPO. Distinct from GMTS (batch top-20% \(|E\cdot\omega|\)).

## Key Contributions
1. Fork-probability envelope as an exponential window over within-response entropy rank.
2. Difficulty damping plus entropy-gated fallback; CreditFilter-D tracks widths online.
3. Three-seed Qwen3-8B-Base DAPO-host bake-off vs DAPO / GRPO.

## Empirical Highlights
Three-seed vs DAPO MATH500 0.860±0.025 vs 0.783±0.107 (+7.7), AIME24 +10.5, AIME25 +9.1. Seed 201 0.876/0.338/0.277 vs DAPO 0.830/0.244/0.177 vs GRPO 0.833/0.263/0.184. 2.1× DAPO tokens at equal steps.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.27227`
- Code: `https://github.com/yoctta/CreditFilter`
