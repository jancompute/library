---
id: paper:rcrl
type: paper
title: 'Rubric Curriculum RL: Exploiting the Generation-Verification Gap in Non-Verifiable Domains'
authors:
- Sumeet Ramesh Motwani
- Tejas Krishnan
- Alistair Letcher
- Charles London
- Suhaas Bhat
- Huitian Jiao
- Philip Torr
- Riashat Islam
- Christopher Summerfield
- Jakob Foerster
- Christian Schroeder de Witt
- Qilong Gu
- Shital Shah
year: 2026
month: 11
arxiv_id: '2611.06244'
url: https://arxiv.org/abs/2611.06244
methods:
- method:rcrl
cites:
- paper:draco
- paper:metarubric
- paper:canopy
tags:
- rubric-rl
- curriculum
- open-ended
- active
---

# Rubric Curriculum RL

## Abstract Summary
RcRL combines pairwise preferences over self-generated rollouts with a curriculum over rubric criteria. Absolute-score rubric RL plateaus; RcRL keeps improving past 1000 steps on creative writing and HealthBench without new data or a stronger teacher.

## Key Contributions
1. Pairwise generation-verification gap instead of absolute rubric scores.
2. Non-stationary criterion curriculum against reward hacking.

## Empirical Highlights
Qwen3-4B 70.5% human win vs base. HealthBench +14.60% / +25.38% vs RaR +8.26% / +7.53%. Does not retarget CANOPY or DRACO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.06244`
- Code: none found (`code_status: none`).
