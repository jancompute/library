---
id: paper:weir
type: paper
title: 'Weir: Watershed Exploration and Drift-Aware Prefix Shrinkage for Multi-Turn Agent Reinforcement Learning'
authors:
- Pixel Nomand
- Elena Voss
- Marcus Hale
- Sofia Reyes
year: 2026
month: 11
arxiv_id: '2611.27570'
url: https://arxiv.org/abs/2611.27570
methods:
- method:weir
cites: []
tags:
- agent-rl
- credit-assignment
- prefix-tree
- multi-turn
---

# Weir: Watershed Exploration and Drift-Aware Prefix Shrinkage for Multi-Turn Agent Reinforcement Learning

## Abstract Summary
Weir keeps a discounted canonical action-prefix tree and trains a prefix critic toward minimax drift-aware shrinkage. Task budgets follow Neyman \(B_q\propto\sqrt{\hat p(1-\hat p)}\); branches go to watershed forks. CAPO is not a library node. No public code. Distinct from CANOPY, TreeHCA, TSBPO.

## Key Contributions
1. Discounted canonical prefix tree plus minimax drift-aware shrinkage critic.
2. Neyman task budgets and watershed forks for within-task branching.
3. 3B/7B QA / ALFWorld / WebShop vs CAPO at 0.71–0.72× tokens.

## Empirical Highlights
3B/7B vs CAPO QA 32.18/37.85 vs 28.99/35.63; ALFWorld 84.83/87.81 vs 81.09/84.33; WebShop 78.47/81.90 vs 76.27/80.40. Author names read as pseudonyms.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.27570`
- Code: none found as of 2026-11-23
