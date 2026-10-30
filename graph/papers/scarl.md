---
id: paper:scarl
type: paper
title: 'SCARL: Sequence Confidence-Aligned Reinforcement Learning'
authors:
- 'Zhenghong Ke'
- 'Jingbo Zhou'
- 'Hua Wu'
year: 2026
month: 10
arxiv_id: '2610.40407'
url: https://arxiv.org/abs/2610.40407
methods:
- method:scarl
cites:
- paper:minimax-m1
tags:
- rlvr
- confidence
- active
---

# SCARL: Sequence Confidence-Aligned Reinforcement Learning

## Abstract Summary
RLVR advantages ignore sequence confidence, so a lucky low-prob success gets the same update as a near-certain one. SCARL reshapes, never re-signs, each advantage by the gap between group-relative confidence and the certified outcome, then shares the class budget. Repairing that gap is also an entropy-collapse remedy.

## Key Contributions
1. Confidence-aligned advantage reshape on GRPO-family RLVR.

## Empirical Highlights
Code github.com/kezhh163/scarl. Reduces to the base estimator when confidence is already aligned. Does not retarget method:cispo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.40407`
- Code: `https://github.com/kezhh163/scarl (`code_status: released`).`
