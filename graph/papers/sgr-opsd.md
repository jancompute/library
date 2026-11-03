---
id: paper:sgr-opsd
type: paper
title: 'SGR-OPSD: Learning from Subgoal Plans with Graph-Regularized Credit Assignment for Agentic Reinforcement Learning'
authors:
- 'Shu Liu'
- 'Yang Chong'
- 'WenShi Chen'
- 'Man Lan'
year: 2026
month: 11
arxiv_id: '2611.02414'
url: https://arxiv.org/abs/2611.02414
methods:
- method:sgr-opsd
cites:
- paper:canopy
- paper:vista
tags:
- opsd
- agents
- active
---

# SGR-OPSD: Learning from Subgoal Plans with Graph-Regularized Credit Assignment for Agentic Reinforcement Learning

## Abstract Summary
Privileged OPSD logp gaps track teacher preference, not task progress. SGR-OPSD converts LLM subgoal plans into KL-regularized advantage weights and calibrates them with a Subgoal Progress Graph of empirical action returns versus the state average.

## Key Contributions
1. Subgoal-plan OPSD with graph-calibrated turn-level credit.

## Empirical Highlights
ALFWorld Qwen2.5-7B 85.8%, up to +7.4 vs GRPO on ALFWorld / WebShop / Search-QA at 3B and 7B.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02414`
- Code: none found (`code_status: none`).
