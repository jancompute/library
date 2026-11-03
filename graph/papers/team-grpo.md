---
id: paper:team-grpo
type: paper
title: 'When Rewards Depend on the Group, GRPO Plays a Tournament'
authors:
- 'Junyi Gao'
- 'Yu Shi'
- 'Pingzhao Hu'
- 'Ewen M Harrison'
year: 2026
month: 11
arxiv_id: '2611.02404'
url: https://arxiv.org/abs/2611.02404
methods:
- method:team-grpo
cites:
- paper:minimax-m1
tags:
- grpo
- diversity
- active
---

# When Rewards Depend on the Group, GRPO Plays a Tournament

## Abstract Summary
When rewards depend on the rest of the group, GRPO's group-relative baseline changes the objective: each response is trained to beat its groupmates with alpha=-1/(K-1). Team-GRPO sets alpha=+1, an unbiased estimator for any group-dependent reward that works with two samples per prompt. On GlobalOpinionQA, GRPO collapses onto the majority (error 0.20, worse than untrained) while Team-GRPO cuts error to 0.08.

## Key Contributions
1. Unbiased group-dependent GRPO with alpha=+1 instead of the tournament baseline.

## Empirical Highlights
GlobalOpinionQA error 0.20 to 0.08 vs GRPO collapse; NoveltyBench avoids diversity collapse. Theory locates 9B fixed points within 0.02 l1; Pearson r=0.995 on concentration.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02404`
- Code: none found (`code_status: none`).
