---
id: paper:tace
type: paper
title: 'Distributional Reward Calibration and Budget-Neutral Credit Assignment for Multimodal RLVR'
authors:
- 'Lang Chen'
- 'Zongxin Xu'
- 'Borui Wang'
- 'Anran Liu'
- 'Shitong Chen'
year: 2026
month: 10
arxiv_id: '2610.40250'
url: https://arxiv.org/abs/2610.40250
methods:
- method:tace
cites:
- paper:corrgrpo
tags:
- rlvr
- credit
- active
---

# Distributional Reward Calibration and Budget-Neutral Credit Assignment for Multimodal RLVR

## Abstract Summary
TACE factorizes GRPO advantages into sample-level baselining and token-level credit. Stage S1 maps verifier rewards to a standard normal with 1D optimal transport. Stage S2 rank-calibrates a stop-grad evidence contrast and renormalizes token weights so they conserve the verifier budget.

## Key Contributions
1. Two-stage OT baseline plus budget-neutral token credit for multimodal RLVR.

## Empirical Highlights
Caps finite-sample outliers; conserves verifier credit. Mention on task:math-code-rl-moe. No public code. Does not retarget method:corrgrpo / method:dara / method:sapo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.40250`
- Code: `none found (`code_status: none`).`
