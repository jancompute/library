---
id: paper:envsched
type: paper
title: 'EnvSched: Environment-Aware Scheduling for Rollout-Efficient Agent Reinforcement Learning'
authors:
- 'Sihan Yang'
- 'Weichen Bai'
- 'Ruichuan An'
- 'Yiming Cheng'
- 'Zhiyuan Feng'
- 'Tianyi Jiang'
- 'Renye Yan'
- 'Ning Ding'
- 'Yifan Zhang'
- 'Renrui Zhang'
- 'Yehui Tang'
- 'Wentao Zhang'
year: 2026
month: 10
arxiv_id: '2610.37609'
url: https://arxiv.org/abs/2610.37609
methods:
- method:envsched
cites:
- paper:sao
tags:
- agentic
- scheduling
- active
---

# EnvSched: Environment-Aware Scheduling for Rollout-Efficient Agent Reinforcement Learning

## Abstract Summary
Finite rollout budgets waste samples on uninformative environment-task pairs. EnvSched learns scheduling value from history, balancing exploitation of reward gaps with coverage of underobserved environments.

## Key Contributions
1. EnvSched as an active env-task scheduler on task:agentic-async-rl.

## Empirical Highlights
Organizes environment-task pairs as a dual-relation graph and schedules from rollout history. Does not retarget method:sao.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37609`
- Code: `none found (`code_status: none`).`
