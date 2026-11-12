---
id: paper:autoscaffold
type: paper
title: 'AutoScaffold: AI-Guided Scaffolding for Reinforcement Learning of Language Models'
authors:
- Zijian Zhang
- Rizhen Hu
- Jiangweizhi Peng
- Shiyang Li
- Sujay Bhatt
- Sihan Zeng
- Mingyi Hong
year: 2026
month: 11
arxiv_id: '2611.14515'
url: https://arxiv.org/abs/2611.14515
methods:
- method:autoscaffold
cites: []
tags:
- rlvr
- scaffolding
- grpo
- active
---

# AutoScaffold: AI-Guided Scaffolding for Reinforcement Learning of Language Models

## Abstract Summary
A frozen teacher turns a student's RLVR training log into class-level strategies and instance-level hints, injected into training prompts and removed at evaluation. Same procedure on ALFWorld (GiGPO), search QA (GiGPO), math (GRPO/DAPO), and KernelBench (rubric GRPO). Scaffold-free eval beats the host RL baseline in every domain. No public trainer as of 2026-11-12.

## Key Contributions
1. Frozen teacher queries training stats, trajectories, and its own past decisions every $K$ steps, then validates class-level edits on held-out tasks before deploy.
2. Class-level strategies plus instance-level hints; injection probability $q[C]\le q_{\max}<1$ so unscaffolded groups remain.
3. Scaffold tokens receive no gradient; the RL algorithm is unchanged.

## Empirical Highlights
ALFWorld $+7.2$ success vs GiGPO; search QA $+4.0$ EM; math up to $+2.0$ avg; KernelBench correctness $+3.0$ / faster-than-PyTorch $+5.0$. Beats QuestA at about one-third the student steps. Removing validation drops ALFWorld by $14.1$. Does not retarget CISPO, CANOPY, or Iris.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.14515`
- Code: none found (`code_status: none`).
