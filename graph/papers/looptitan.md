---
id: paper:looptitan
type: paper
title: 'LoopTitan: Parameter Revisit Buys Almost Nothing in Looped LLM Pretrain'
authors:
- Zichen Tian
- Yudong Lu
- Xuansheng Wu
- Na Zou
- Xia Hu
- Guanchu Wang
- Qianru Sun
year: 2026
month: 11
arxiv_id: '2611.34821'
url: https://arxiv.org/abs/2611.34821
methods:
- method:smelt
- method:gated-loop-moe
cites:
- paper:smelt
- paper:gated-loop-moe
- paper:elr
- paper:looped-models-done-right
- paper:no-free-loop
tags:
- looped-lm
- pretrain
- gotcha
---

# LoopTitan: Parameter Revisit Buys Almost Nothing in Looped LLM Pretrain

## Abstract Summary
Looped-Transformer pretrain gains are mostly from shape and optimizer, not from revisiting the same parameters. LoopTitan-Base (non-revisit reshape under Muon) matches the looped recipe; extra revisits add almost nothing. Distinct from SMELT (compute-matched middle-layer MoE looping), Gated-Loop MoE, ELR mixed-depth, and Huginn-style fixed-point loops. Complements `paper:no-free-loop` (post-train loops).

## Key Contributions
1. Isolates parameter revisit from depth/width reshape and optimizer on a shared LoopTitan family.
2. LoopTitan-Base under Muon matches the looped recipe; revisit is not the kernel.
3. Releases 17 models (MIT). Code datamllab/LoopTitan.

## Empirical Highlights
Parameter revisit is near-zero once shape and Muon are matched. Gains attributed to looping in prior recipes can be recovered by a non-revisit baseline of the same shape. Homepage datamllab.github.io/LoopTitan/. Does not retarget SMELT, Gated-Loop MoE, ELR, or Looped Models Done Right.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.34821`
- Code: `https://github.com/datamllab/LoopTitan`
- Homepage: `https://datamllab.github.io/LoopTitan/`
