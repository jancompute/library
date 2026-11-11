---
id: paper:lcs-opd
type: paper
title: 'Which Successes Make Good References? Action-Sequence Alignment for Multi-Turn On-Policy Distillation'
authors:
- Mufei Li
- Nikki Lijing Kuang
- Zhuoer Wang
- Samson Koelle
- Jie Yuan
- Manqing Mao
- Hong Wang
- Yanjun Lin
- James Feng
- Daniel Edmiston
- Pan Li
- Wei Niu
year: 2026
month: 11
arxiv_id: '2611.13135'
url: https://arxiv.org/abs/2611.13135
methods:
- method:lcs-opd
cites:
- paper:opd
tags:
- distillation
- opd
- agents
- reference-selection
- active
---

# Action-Sequence Alignment for Multi-Turn On-Policy Distillation

## Abstract Summary
Successful traces of the same multi-turn task are not interchangeable as OPD references. LCS-OPD assigns each failed student trajectory the success with the longest common action subsequence and updates only on failures. On ALFWorld Valid Unseen, Qwen2.5-3B $78.4\to 85.8$ and 7B $83.6\to 94.0$ vs vanilla OPD. No public code as of 2026-11-11.

## Key Contributions
1. Free-target OT reduces to nearest-success assignment under pairwise compatibility.
2. Normalized LCS over executed actions, not observations or prefixes.
3. Failure-only OPD: scoring successful student rollouts against a reference hurts.

## Empirical Highlights
LCS is the only of eight selectors to beat vanilla OPD on every aggregate for both students. Airline Pass^4 $30.0\to 41.7$ (2B) / $26.7\to 38.3$ (4B); retail transfer Pass^1 $70.4\to 78.3$ / $56.2\to 69.4$. Does not retarget CANOPY.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.13135`
- Code: none found (`code_status: none`).
