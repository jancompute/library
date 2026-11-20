---
id: paper:hisa-rope
type: paper
title: 'HiSA: Sparsifying the Hidden Dimension of RoPE Attention in LLMs'
authors:
- Ambroise Borbely
- Mathieu Salzmann
- Olivier Verscheure
year: 2026
month: 11
arxiv_id: '2611.26363'
url: https://arxiv.org/abs/2611.26363
methods:
- method:hisa-rope
cites: []
tags:
- sparse-attention
- pretrain
- hisa
---

# HiSA: Sparsifying the Hidden Dimension of RoPE Attention in LLMs

## Abstract Summary
HiSA trains sparse QK from scratch (and converts dense checkpoints) with a RoPE-compatible hidden sparsity pattern. Distinct from AF1's HiSA (1-bit PTQ). Flash-HiSA matches FA3 throughput at lower QK density. Concurrent ATFlash / WavePrune are mentioned, not ingested.

## Key Contributions
1. From-scratch sparse QK at 135M/360M with val-loss wins at 20–35% QK.
2. Dense-to-sparse conversion path under `task:posttrain-attention-sparsification`.
3. Flash-HiSA kernel vs FA3 tokens/s.

## Empirical Highlights
135M 4K val 2.880 vs dense 2.906 at 29.3% of QK. 360M 2.575 vs 2.587. Flash-HiSA 2.892 vs FA3 2.904, 238k vs 236k tok/s, ρ=34.8%. 16K exact PG19 3.170 vs 3.205 at 20.2% QK.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.26363`
- Code: `https://github.com/ambroise-b/hisa`
