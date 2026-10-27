---
id: paper:intra
type: paper
title: 'INTRA: Interleaved Non-contiguous Token spaRse Attention'
authors:
- 'Yuxuan Xia'
- 'Wenbo Lu'
- 'Shaoyi Zheng'
- 'Shengjie Wang'
year: 2026
month: 10
arxiv_id: '2610.34056'
url: https://arxiv.org/abs/2610.34056
methods:
- method:intra
cites:
- paper:sas
tags:
- sparse-attention
- active
---

# INTRA: Interleaved Non-contiguous Token spaRse Attention

## Abstract Summary
Static hardware-aware sparse attention with Scatter/Gather relay groups so sparse layers keep global reachability under Computational Query Set constraints. Code NovTi/INTRA.

## Key Contributions
1. INTRA as an active plug-in on task:posttrain-attention-sparsification.

## Empirical Highlights
CQS-compatible Flash patterns with global reachability via complementary sparse groups. Does not retarget method:sas.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34056`
- Code: `https://github.com/NovTi/INTRA (`code_status: released`).`
