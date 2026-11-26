---
id: paper:gated-loop-moe
type: paper
title: Gated-Loop Mixture-of-Experts
authors:
- Shipeng Bai
- Jiayu Qin
- Hong Liu
- Xili Wang
- Jianchao Tan
- Jiacheng Li
- He Zhang
- Yifan Lu
- Jiaqi Zhang
- Kefeng Zhang
- Yuchen Xie
- Xunliang Cai
year: 2026
month: 11
arxiv_id: '2611.34276'
url: https://arxiv.org/abs/2611.34276
methods:
- method:gated-loop-moe
cites: []
tags:
- architecture
- moe
- looped
---

# Gated-Loop Mixture-of-Experts

## Abstract Summary
Gated-Loop MoE applies gated inner-loop state updates plus a Prelude-to-Coda residual. The Core is 25–35% of unrolled depth; saved parameters buy extra routed experts. Distinct from SMELT (middle 50% twice under matched FLOPs/params/KV), ELR (mixed-depth dense loops), and MoLT (KV-as-memory looping). The 200B PPL listing vs named looped methods is not SMELT's Chinchilla protocol.

## Key Contributions
1. Gated inner-loop state updates with a Prelude-to-Coda residual.
2. Recurrence confined to a Core block; reallocate saved params to extra experts.
3. 1T-token 69B MLA / 51B KDA vs budget-matched non-recurrent; 200B reproduction vs other looped recipes.

## Empirical Highlights
After 1T tokens, 69B MLA +1.16pp and 51B KDA +2.29pp vs budget-matched non-recurrent. 200B reproduction reports lower PPL than other looped methods named in the listing (Parcae, SMELT). GitHub announced URL 404 as of 2026-11-26.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.34276`
- Code: announced, GitHub 404 as of 2026-11-26
