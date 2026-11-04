---
id: paper:dory
type: paper
title: 'Dory: nGPT Looped Pretrain with Difficulty-Aware Loops'
authors:
- 'Maxim Fishman'
- 'Simeng Sun'
- 'Shantanu Acharya'
- 'Faisal Ladhak'
- 'Brian Chmiel'
- 'Santiago Akle Serano'
- 'Ron Banner'
- 'Boris Ginsburg'
- 'Krishna C. Puvvada'
year: 2026
month: 11
arxiv_id: '2611.03998'
url: https://arxiv.org/abs/2611.03998
methods:
- method:dory
cites:
- paper:elr
- paper:quartet-ii
tags:
- architecture
- looped-lm
- nvfp4
- active
---

# Dory: nGPT Looped Pretrain with Difficulty-Aware Loops

## Abstract Summary
Dory1.0-4B is an nGPT looped LM trained on 6T tokens (4.5T NVFP4) with a difficulty-aware loop curriculum and last-loop KV. 12-bench avg 35.2 (k=1) → 39.7 (k=2) → 40.6 (k=4). Open weights at nvidia/nemotron-labs-dory.

## Key Contributions
1. nGPT looped 4B with difficulty-aware loop curriculum.
2. 4.5T of 6T tokens in NVFP4; last-loop KV.

## Empirical Highlights
12-bench avg 35.2 (k=1) → 39.7 (k=2) → 40.6 (k=4).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03998`
- Weights: `https://huggingface.co/collections/nvidia/nemotron-labs-dory`
- Official train code: none found (`code_status: none`). Unofficial ports exist.
