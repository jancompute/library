---
id: paper:loopback-transformer
type: paper
title: 'Loopback Transformer: Towards a Unified View of Residual Looped Transformers'
authors:
- Xuan Ouyang
- Zefan Cai
- Chenlong Zhang
- Cheng Luo
- Ke Wan
- Junjie Hu
year: 2026
month: 11
arxiv_id: '2611.07226'
url: https://arxiv.org/abs/2611.07226
methods:
- method:loopback-transformer
cites: []
tags:
- architecture
- looped-lm
- residual
- active
---

# Loopback Transformer: Towards a Unified View of Residual Looped Transformers

## Abstract Summary
Looped Transformers share blocks, but sharing does not decide which residual to store or how later reads weight it. Loopback stores each block update, keeps the stack input on a separate path, and reads updates with geometric decay plus attention. ClimbMix 191M–3B at 40–75% Transformer params (excluding embeddings and head), tokens and executed depth matched. Code yancyou/Loopback. Does not retarget Muon2 or ELR.

## Key Contributions
1. Residual-update memory with separate controls for input strength, total update weight, and allocation.
2. Geometric decay supplies a recency prior; attention allocates that weight.
3. Lower ClimbMix val loss than Standard plus seven looped residual designs at 191M/374M/778M.

## Empirical Highlights
191M 2.6187 vs Standard 2.6234; 374M 2.4008 vs 2.4395; 778M 2.2404 vs 2.2644. 3B WikiText 16.74 vs 17.28; 13-task mean 49.45%. Extra visits 50.17% vs a larger loss rise on Plain Loop.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.07226`
- Code: `https://github.com/yancyou/Loopback` (`code_status: released`).
- Project: `https://yancyou.github.io/Loopback_page/`
