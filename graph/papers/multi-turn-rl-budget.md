---
id: paper:multi-turn-rl-budget
type: paper
title: 'What Does Multi-Turn Reinforcement Learning Really Improve in LLM Agents?'
authors:
- Kejian Zhu
- Zhuoran Jin
- Shangqing Tu
- Tianyi Men
- Yupu Hao
- Jiachun Li
- Kang Liu
- Jun Zhao
year: 2026
month: 11
arxiv_id: '2611.06483'
url: https://arxiv.org/abs/2611.06483
methods:
- method:canopy
- method:sao
cites:
- paper:canopy
- paper:sao
- paper:agentic-self-distill-reality
tags:
- agentic
- multi-turn
- gotcha
---

# What Does Multi-Turn Reinforcement Learning Really Improve in LLM Agents?

## Abstract Summary
Trajectory-level gains from multi-turn agentic RL need a large interaction budget T. Under tight T the advantage shrinks or reverses. Step-level action quality is not uniformly better (DeepCoder-MT 46.8% / FrozenLake 42.8% of matched states favor RL). Strength concentrates in error recovery (65.7–67.3% of error states) and later turns. BudgetMix is a preliminary training mix in the paper, not a library method.

## Key Contributions
1. Pass@(K,T) splits sampling breadth from interaction depth.
2. Multi-turn RL mainly buys error recovery and long-horizon composition, not per-step quality.

## Empirical Highlights
Gotcha on `task:outcome-only-long-horizon-agent-rl` with a mention on `task:agentic-async-rl`. Complements `paper:agentic-self-distill-reality` / `paper:credit-helps-hurts`. Does not retarget CANOPY or SAO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.06483`
- Project: `https://rethinking-agentic-rl.github.io/`
- Code: none found (`code_status: none`).
