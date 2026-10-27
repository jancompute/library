---
id: paper:sepo
type: paper
title: 'Self-Evolution Reasoner: Continuous Optimization via Policy-Intrinsic Exploration and Exploitation'
authors:
- 'Wenhang Shi'
- 'Yiren Chen'
- 'Zhe Zhao'
- 'Jinhao Dong'
- 'Wei Lu'
- 'Xiaoyong Du'
year: 2026
month: 10
arxiv_id: '2610.34137'
url: https://arxiv.org/abs/2610.34137
methods:
- method:sepo
cites:
- paper:minimax-m1
- paper:opd
tags:
- rlvr
- active
---

# Self-Evolution Reasoner: Continuous Optimization via Policy-Intrinsic Exploration and Exploitation

## Abstract Summary
RLVR and OPSD stall when the policy never samples a valid solution. SEPO uses labels to elicit in-distribution reasoning, then distills that newly found solution back as a self-teacher.

## Key Contributions
1. SEPO as an active plug-in on task:math-code-rl-dense.

## Empirical Highlights
Best under matched time or steps on scientific, tool-use, and logical reasoning. Does not retarget method:cispo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34137`
- Code: `none found (`code_status: none`).`
