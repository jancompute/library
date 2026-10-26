---
id: paper:gs-moe
type: paper
title: 'GS-MoE: Training-Free MoE Compression via Groupwise Subspace Sharing and Pruning'
authors:
- 'Carson Cary'
- 'Yukai Jin'
- 'Yihao Huang'
- 'Zhankai Ye'
- 'Fangyi Li'
- 'Ting Hua'
- 'Xin Liu'
- 'Shangqian Gao'
year: 2026
month: 10
arxiv_id: '2610.32009'
url: https://arxiv.org/abs/2610.32009
methods:
- method:gs-moe
cites:
- paper:deepseek-v4
- paper:spare-moe
tags:
- moe
- compression
- active
---

# GS-MoE

## Abstract Summary
MoE compute is sparse but expert storage is not. GS-MoE is training-free compression along shared-subspace rank and expert intermediate width.

## Key Contributions
1. GS-MoE as an active plug-in on task:pretrain-moe-frontier.

## Empirical Highlights
- Training-free groupwise subspace share + width prune. Does not retarget method:deepseek-v4 or method:spare-moe.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.32009`
- Code: `https://github.com/cbacary/GS-MoE` (`code_status: released`).
