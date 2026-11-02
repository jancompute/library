---
id: paper:li2sao
type: paper
title: 'Li2SAO: Lifting Light Single-Rollout Asynchronous RL Optimization via Group-Relative Actor-Critic Bootstrapping'
authors:
- 'Zichen Bai'
- 'Yanli Wang'
- 'Yang Liu'
- 'Junhao Shi'
- 'Xueqin Liu'
- 'Jinguo Sun'
- 'Muye Li'
- 'Shaoqiang Zheng'
- 'Xuefei Diao'
- 'Zhuwei Zeng'
- 'Nan Duan'
- 'Peng Cao'
year: 2026
month: 10
arxiv_id: '2610.40726'
url: https://arxiv.org/abs/2610.40726
methods:
- method:li2sao
cites:
- paper:sao
tags:
- async-rl
- actor-critic
- active
---

# Li2SAO: Lifting Light Single-Rollout Asynchronous RL Optimization via Group-Relative Actor-Critic Bootstrapping

## Abstract Summary
SAO needs a closed-source pretrained value model. A lightweight SAO without that critic (LiSAO) loses to GRPO on single-turn reasoning and lags early because the critic is cold. Li2SAO bootstraps: while the critic is cold, a group-relative advantage trains the actor and a group-centered return trains the critic, then training switches to single-rollout GAE. It catches GRPO early and raises the later ceiling on agentic tasks.

## Key Contributions
1. Group-relative actor-critic bootstrap for single-rollout async RL without a pretrained value model.

## Empirical Highlights
Code github.com/jd-cc-coder/Li2SAO (slime). Does not retarget method:sao.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.40726`
- Code: `https://github.com/jd-cc-coder/Li2SAO` (`code_status: released`).
