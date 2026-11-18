---
id: paper:rsc
type: paper
title: Regularized Score Centering
authors:
- Hao Bai
- Chenlu Ye
- Xuanchang Zhang
- Aviral Kumar
- Tong Zhang
year: 2026
month: 11
arxiv_id: '2611.21791'
url: https://arxiv.org/abs/2611.21791
methods:
- method:rsc
cites: []
tags:
- async-rl
- importance-sampling
- score-centering
- active
---

# Regularized Score Centering

## Abstract Summary
Score centering (SC) removes reward-baseline effects under stale/off-policy IS, but fails when the learner leaves the behavior policy. Regularized Score Centering (RSC) adds reverse-KL next-token matching to SC, with or without truncated IS. AppWorld mean +14.3% over SC and SC+TIS; BabyAI 9.9× IS-PPOClip; top of six agentic tasks with RSC+TIS. Upgrades `paper:score-centering-pg` into a trainer; does not supersede that note. GitHub BiEchi/rsc is empty (`code_status: announced`). Project biechi.github.io/blog/rsc/. Does not retarget SAO, CISPO, or DLC.

## Key Contributions
1. Reverse-KL regularizer on score centering so the learner stays near the behavior next-token distribution.
2. Works with or without truncated IS; theory ties KL control to surrogate-to-reward improvement.
3. Agentic evals under stale policies: shopping, tools, games, and fully async software engineering.

## Empirical Highlights
RSC (TIS) AppWorld dev 14.04 vs SC/SC+TIS 12.28 (+14.3%). BabyAI 18.06 vs IS-PPOClip 1.83 (9.9×). Crafter 14.21 vs 9.34; Craftax 4.71 vs 4.04.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.21791`
- Project: `https://biechi.github.io/blog/rsc/`
- Code: `https://github.com/BiEchi/rsc` (`code_status: announced`; size 0 as of 2026-11-18).
