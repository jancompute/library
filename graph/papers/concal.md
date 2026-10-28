---
id: paper:concal
type: paper
title: 'Action-Value Calibration via Continuation Sharing for Long-Horizon Agentic Reinforcement Learning'
authors:
- 'Yingjian Chen'
- 'Lang Zhou'
- 'Zixin Zhao'
- 'Pingfan Li'
- 'Weishi Zheng'
- 'Zhilin Zhao'
year: 2026
month: 10
arxiv_id: '2610.37195'
url: https://arxiv.org/abs/2610.37195
methods:
- method:concal
cites:
- paper:canopy
tags:
- rlvr
- agentic
- active
---

# Action-Value Calibration via Continuation Sharing for Long-Horizon Agentic Reinforcement Learning

## Abstract Summary
GiGPO-style estimators score each action from one continuation. ConCal reuses other visits' continuations already in the batch, matches incoming transitions, and backups calibrated values without extra rollouts.

## Key Contributions
1. ConCal as an active continuation-sharing plug-in on task:outcome-only-long-horizon-agent-rl.

## Empirical Highlights
Qwen2.5-1.5B-Instruct ALFWorld/WebShop +3.39/+5.86pp vs GiGPO. Does not retarget method:canopy.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37195`
- Code: `https://github.com/Yingjian-Chen/ConCal (`code_status: released`).`
