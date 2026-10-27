---
id: paper:mpo
type: paper
title: 'Multiscale Policy Optimization for Long-Horizon LLM Agents'
authors:
- 'Tao Ren'
- 'Hui Yang'
- 'Jia Deng'
- 'Tingyang Chen'
- 'Qiyao Wang'
- 'Shuo Tang'
- 'Ziyang Zeng'
- 'Yuhua Jiang'
- 'Guanghao Li'
- 'Huatong Song'
- 'Yining Li'
- 'Yifan Luo'
year: 2026
month: 10
arxiv_id: '2610.35013'
url: https://arxiv.org/abs/2610.35013
methods:
- method:mpo
cites:
- paper:canopy
- paper:sao
tags:
- rlvr
- agentic
- active
---

# Multiscale Policy Optimization for Long-Horizon LLM Agents

## Abstract Summary
Critic values on long-horizon agents move mostly across turns. MPO estimates advantages at turn scale and applies turn-level importance sampling, then splits credit among tokens.

## Key Contributions
1. MPO as an active plug-in on task:outcome-only-long-horizon-agent-rl with a mention on task:agentic-async-rl.

## Empirical Highlights
Search, tool-use, and automation with 4B and 30B-A3B: consistent gains over strong RL baselines. Does not retarget method:canopy or method:sao.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.35013`
- Code: `none found (`code_status: none`).`
