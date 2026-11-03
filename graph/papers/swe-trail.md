---
id: paper:swe-trail
type: paper
title: 'SWE-Trail: History-Guided Trajectory Collection for Coding Agent Training'
authors:
- 'Ziming Li'
- 'Lu Yu'
- 'Jiatan Huang'
- 'Qing Cui'
- 'Jun Zhou'
- 'Chuxu Zhang'
year: 2026
month: 11
arxiv_id: '2611.02074'
url: https://arxiv.org/abs/2611.02074
methods:
- method:swe-trail
cites:
- paper:codemidas
tags:
- swe
- trajectories
- active
---

# SWE-Trail: History-Guided Trajectory Collection for Coding Agent Training

## Abstract Summary
Independent multi-sample SWE trajectories get redundant. Exposing collection history as advice creates a train-test mismatch. SWE-Trail keeps history outside the agent's context: it picks a checkpoint where more collection may help, the agent proposes next actions from its ordinary context, and SWE-Trail briefly executes them from the same checkpoint to choose a route.

## Key Contributions
1. History-guided SWE trajectory collection that never puts history in the training agent's context.

## Empirical Highlights
124B student +2.33 / +1.60 pp vs independent sampling on SWE-bench Multilingual / Pro.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02074`
- Code: none found (`code_status: none`).
