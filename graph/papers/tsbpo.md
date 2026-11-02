---
id: paper:tsbpo
type: paper
title: 'TSBPO: Tree-Structured Branching for Policy Optimization in Interactive Language Agents'
authors:
- Rui Yu
- Chong Mu
- Jinchuan Zhang
year: 2026
month: 10
arxiv_id: '2610.41697'
url: https://arxiv.org/abs/2610.41697
methods:
- method:tsbpo
cites:
- paper:canopy
tags:
- agent-rl
- tree
- active
---

# TSBPO: Tree-Structured Branching for Policy Optimization in Interactive Language Agents

## Abstract Summary
TSBPO trains interactive agents from terminal outcomes with one sampling-to-update loop. A likelihood-fitted Root/Branch allocator spends a fixed rollout budget on continuations likely to contrast. Trajectory advantages compare sibling segments; observation-group step advantages compare matched task/observation states. The actor sums clipped token surrogates over each complete response and normalizes across active turns. Qwen2.5-1.5B: ALFWorld 97.79% seen / 96.64% unseen; WebShop 81.07% over six stochastic episodes on 500 test goals.

## Key Contributions
1. Tree Root/Branch allocator plus sibling and observation-group advantages for outcome-only agent RL.

## Empirical Highlights
No public code as of 2026-11-02. WebShop step-term ablation 75.93% at the same update-100 eval. Does not retarget method:canopy.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.41697`
- Code: none found (`code_status: none`).
