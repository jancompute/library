---
id: paper:rlid
type: paper
title: 'RLiD: Reinforcement Learning in the Decision Plane for Language Agents and LLMs'
authors:
- 'Ziyi Chen'
- 'Yan Zhang'
- 'Jianhui Wei'
- 'Jianing Yin'
- 'Daoan Zhang'
year: 2026
month: 11
arxiv_id: '2611.02455'
url: https://arxiv.org/abs/2611.02455
methods:
- method:rlid
cites:
- paper:canopy
- paper:sao
tags:
- agents
- decision-rl
- active
---

# RLiD: Reinforcement Learning in the Decision Plane for Language Agents and LLMs

## Abstract Summary
Token-level RL credits whole responses, including parse tokens and malformed text. RLiD compiles observations, optional memory, and a labeled action menu, then a large decision model selects an action in one forward pass. Invalid actions disappear. Trained LDM policies can be distilled into generative LLMs on action trajectories.

## Key Contributions
1. Decision-plane RL that optimizes executable action probabilities instead of tokens.

## Empirical Highlights
ALFWorld 99.3% in 12.7 H100-h vs token-level 86.6% in 17.3h; with compact memory 100% on 134 unseen tasks. Also ARC / Countdown / Sokoban.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02455`
- Code: none found (`code_status: none`).
