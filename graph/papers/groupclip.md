---
id: paper:groupclip
type: paper
title: 'GroupClip: Decoupled Embedding Clipping for Gated Sequence Models'
authors:
- 'Xin Liu'
- 'Boyuan Sun'
- 'Yuxin Wang'
- 'Haoran Song'
- 'Mingjian Zhao'
- 'Mengyu Liu'
year: 2026
month: 11
arxiv_id: '2611.04449'
url: https://arxiv.org/abs/2611.04449
methods:
- method:groupclip
cites:
- paper:mamba-2-paper
tags:
- architecture
- ssm
- active
---

# GroupClip: Decoupled Embedding Clipping for Gated Sequence Models

## Abstract Summary
Near-zero untied embeddings stall gated models (Mamba / GDN / xLSTM). 52.6% of 38 untied gated checkpoints hit the stall; FP32 clip overflow zeros batch grads on ~20% of steps in Nemotron-3-Nano-4B Telugu CPT. GroupClip is a 3-line decoupled embedding clip. GateFloor (SiLU(z)+δ) is the from-scratch companion in the same paper.

## Key Contributions
1. Diagnose near-zero embedding stalls in gated sequence models.
2. GroupClip decoupled embedding clip; GateFloor for from-scratch runs.

## Empirical Highlights
52.6% of 38 untied gated checkpoints stall. FP32 clip overflow zeros batch grads ~20% of steps on Nemotron-3-Nano-4B Telugu CPT.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.04449`
- Code: none found (`code_status: none`).
