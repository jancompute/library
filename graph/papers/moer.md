---
id: paper:moer
type: paper
title: 'MOER: Mix-Policy Optimization under Expert Prefix Guidance with Selective Rollback'
authors:
- 'Xuyang Zhong'
- 'Jiuding Yang'
- 'Yiwen Guo'
- 'Chen Liu'
year: 2026
month: 10
arxiv_id: '2610.30873'
url: https://arxiv.org/abs/2610.30873
methods:
- method:moer
cites:
- paper:minimax-m1
tags:
- rlvr
- mix-policy
- active
---

# MOER

## Abstract Summary
Mix-policy optimization can ingest expert data, but static full-trace guidance suppresses exploration and unguarded prefixes can collapse training. MOER uses expert prefix guidance with selective rollback.

## Key Contributions
1. MOER as an active plug-in on task:math-code-rl-dense.

## Empirical Highlights
- Selective rollback of unhelpful expert prefixes. Does not retarget method:cispo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.30873`
- Code: `https://github.com/CityU-MLO/MOER` (`code_status: released`).
