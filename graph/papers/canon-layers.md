---
id: paper:canon-layers
type: paper
title: 'Physics of Language Models: Part 4.2, Canon Layers at Scale where Synthetic Pretraining Resonates in Reality'
authors:
- Zeyuan Allen-Zhu
year: 2026
month: 11
arxiv_id: '2611.24963'
url: https://arxiv.org/abs/2611.24963
methods:
- method:canon-layers
cites: []
tags:
- architecture
- pretrain
- canon
- gla
- mamba
---

# Physics of Language Models: Part 4.2, Canon Layers at Scale where Synthetic Pretraining Resonates in Reality

## Abstract Summary
64 from-scratch 1.3B–8B runs on 1–2T Nemotron-CC tokens. Canon layers (local token mixing, <0.2% params) save about 30% of pretraining tokens for the same 8B MMLU. GLA5 and GDN2 replace full-rank output gates with rank-16 gates and reallocate the saved parameters. With Canon, GLA5 matches GDN2 and beats strictly aligned Mamba2 at 8B/1T. Linear models that match Transformers on lm-eval still fail short-context retrieval.

## Key Contributions
1. Canon layers on every Llama sublayer: 8B/1T lm-eval/MMLU 67.7/62.4 vs Llama 66.9/60.6.
2. GLA5 / GDN2 low-rank output gates under strict parameter/memory alignment with Mamba2.
3. Horizontal mixing dominates extra recurrent machinery once Canon is present.

## Empirical Highlights
LlamaCanon matches Llama-3.1-8B using 1/15 of its training tokens. Vanilla 8B Llama scores +2.5 vs Nvidia's Transformer on the same data. GLA5+Canon 8B/1T lm-eval/MMLU 68.0/63.0 vs Mamba2 67.3/61.6 vs GDN2+Canon 68.2/64.0.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.24963`
- Code: `https://github.com/facebookresearch/PhysicsLM4`
