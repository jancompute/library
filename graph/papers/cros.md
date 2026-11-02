---
id: paper:cros
type: paper
title: 'CRoS: Causality Reward on Scrambled CoTs Improves Accuracy and Reasoning Faithfulness'
authors:
- Xiao Yu
- Justin Chih-Yao Chen
- Zaid Khan
- Hyunji Lee
- Mohit Bansal
year: 2026
month: 10
arxiv_id: '2610.42054'
url: https://arxiv.org/abs/2610.42054
methods:
- method:cros
cites:
- paper:minimax-m1
tags:
- rlvr
- causality
- active
---

# CRoS: Causality Reward on Scrambled CoTs Improves Accuracy and Reasoning Faithfulness

## Abstract Summary
Outcome-only RLVR does not guarantee that the CoT caused the answer. Deletion/error-injection causality metrics confound information change with true causality and, as rewards, shrink informative CoTs. CRoS scrambles step order without changing step content. On Reasoning Gym with Gemma-3-4B it reaches 46.8% on five unseen logic/games sets vs 43.8% strongest baseline, CoT-Pass@K 43.4 vs 41.4 (K=1 to 128), and hint acknowledgment 34.0 vs 20.2.

## Key Contributions
1. Order-scramble CoT causality reward that preserves step content.

## Empirical Highlights
Project xxiaoyuuuu.github.io/CRoS-Page. No public GitHub as of 2026-11-02. Does not retarget method:cispo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.42054`
- Project: `https://xxiaoyuuuu.github.io/CRoS-Page`
- Code: none found (`code_status: none`).
