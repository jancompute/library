---
id: paper:self-steered-reasoner
type: paper
title: 'Steer, Don''t Tell: Breaking Reasoning Plateaus with Reachability-Aligned Self-Distillation'
authors:
- 'Zijian Wu'
- 'Lingkai Kong'
- 'Lin Yang'
- 'Haiteng Zhao'
- 'Kuikun Liu'
- 'Kai Chen'
- 'Dahua Lin'
- 'Wenwei Zhang'
year: 2026
month: 11
arxiv_id: '2611.00796'
url: https://arxiv.org/abs/2611.00796
methods:
- method:self-steered-reasoner
cites:
- paper:vista
tags:
- opsd
- reachability
- active
---

# Steer, Don't Tell: Breaking Reasoning Plateaus with Reachability-Aligned Self-Distillation

## Abstract Summary
Privileged self-teachers that condition on a reference solution can emit trajectories the unprivileged student cannot reach. Self-Steered Reasoner (SSR) projects the privileged teacher onto locally reachable student actions, verifies those trajectories, and iteratively refines with diagnostic guidance. Distinct from method:ssr (successive scale racing).

## Key Contributions
1. Reachability-aligned privileged self-distillation via student-support projection.

## Empirical Highlights
On problems with pass@64=0 after extensive RL, recovers correct and learnable trajectories for 74.6% without a parallel expert; +4.9pp on AIME25/26+HMMT26.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.00796`
- Code: none found (`code_status: none`). Distinct from method:ssr.
