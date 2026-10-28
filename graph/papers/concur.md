---
id: paper:concur
type: paper
title: 'CONCUR: Concordant Auxiliary Rewards for Multi-Task, Multi-Reward Reinforcement Learning'
authors:
- 'Jixuan Leng'
- 'Si Si'
- 'Fei Wang'
- 'Cho-Jui Hsieh'
- 'Jiong Zhang'
- 'Hsiang-Fu Yu'
- 'Inderjit S. Dhillon'
year: 2026
month: 10
arxiv_id: '2610.36437'
url: https://arxiv.org/abs/2610.36437
methods:
- method:concur
cites:
- paper:corrgrpo
tags:
- rlvr
- multi-reward
- active
---

# CONCUR: Concordant Auxiliary Rewards for Multi-Task, Multi-Reward Reinforcement Learning

## Abstract Summary
Gated auxiliaries can reverse a group's primary order under group-relative advantages. CONCUR projects those scores to the closest primary-monotone, ceiling-tied vector. CONCUR-T keeps both constraints; CONCUR-A lifts the ceiling tie.

## Key Contributions
1. CONCUR as an active gated-auxiliary plug-in on task:multi-reward-rlvr.

## Empirical Highlights
Keeps auxiliaries from reversing the primary without the keep-vs-drop task split. Does not retarget method:corrgrpo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36437`
- Code: `none found (`code_status: none`).`
