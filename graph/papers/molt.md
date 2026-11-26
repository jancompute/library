---
id: paper:molt
type: paper
title: Mixture-of-Loops Transformer
authors:
- Lianghui Zhu
- Shijie Wang
- Xinggang Wang
- Jinze Bai
- Bo Wang
- Xiang Bai
year: 2026
month: 11
arxiv_id: '2611.34923'
url: https://arxiv.org/abs/2611.34923
methods:
- method:molt
cites: []
tags:
- architecture
- looped-transformer
- kv-memory
---

# Mixture-of-Loops Transformer

## Abstract Summary
MoLT treats keys and values as the loop memory. MoLT-R keeps the residual stream and reads local KV across loops. MoLT-KV restarts from embeddings and mixes current-loop local KV with preceding-loop memory KV. U-MoLT splits memory construction from prediction readout so unused decoder traversals can be skipped. Distinct from mixed-depth ELR and from SMELT middle-layer looping.

## Key Contributions
1. Mixture-of-Loops Attention (MoLA) with KV as selective loop memory.
2. MoLT-R vs MoLT-KV plus loop forcing for single-traversal MoL decode past the train horizon.
3. U-MoLT encoder-decoder split with MoL-Hybrid-2 latency matching OLMo3.

## Empirical Highlights
400B-token pretrain: U-MoLT beats OLMo3 at 700M / 1.5B dense and 3B MoE; 1.7× val CE token efficiency at 700M; 3B MoE 10-domain PPL −0.75 and 10-task +2.1pp. Qwen3.5-0.8B-Base 100B CPT 1.4× mean token efficiency. S-size (~113M) MoL-Hybrid-2 996.6 vs 1,000.6 ms.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.34923`
- Code: `https://github.com/hustvl/MoLT`
