---
id: paper:coharl
type: paper
title: 'CoHARL: Co-Evolving Agent Policies and Executable Harnesses with Reinforcement Learning'
authors:
- 'Jianwen Chen'
- 'Peng Xia'
- 'Kaide Zeng'
- 'Siwei Han'
- 'Zhen-Yu Zhang'
- 'Charles Fleming'
- 'Xinyu Ye'
- 'Huaxiu Yao'
year: 2026
month: 10
arxiv_id: '2610.36469'
url: https://arxiv.org/abs/2610.36469
methods:
- method:coharl
cites:
- paper:self-hpo
- paper:harness-elicitation-expansion
tags:
- agents
- harness
- active
---

# CoHARL: Co-Evolving Agent Policies and Executable Harnesses with Reinforcement Learning

## Abstract Summary
Fixing the harness while the policy learns, or searching a harness once, leaves the interface stale. CoHARL trains a shared policy on a population of executable harnesses and revises harness code from traces.

## Key Contributions
1. CoHARL as an active harness-population RL plug-in on task:agent-harness-runtime.

## Empirical Highlights
SWE-rebench 27.6% mean resolved (+6.4pp vs harness-only). Does not retarget method:omp2-harness or method:self-hpo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36469`
- Code: `none found (`code_status: none`).`
