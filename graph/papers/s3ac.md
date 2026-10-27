---
id: paper:s3ac
type: paper
title: 'S3AC: Stabilized, Selective, and Scalable Actor-Critic for LLM Reasoning'
authors:
- 'Shuo Shen'
- 'Guangran Cheng'
- 'Chengqi Lyu'
- 'Xiangsen Wang'
- 'Yanan Sun'
- 'Wenwei Zhang'
year: 2026
month: 10
arxiv_id: '2610.35518'
url: https://arxiv.org/abs/2610.35518
methods:
- method:s3ac
cites:
- paper:bpco
- paper:minimax-m1
tags:
- rlvr
- actor-critic
- active
---

# S3AC: Stabilized, Selective, and Scalable Actor-Critic for LLM Reasoning

## Abstract Summary
Long-CoT critic training fails from length coverage and early value-head gradients. S3AC is a critic recipe with token-specific advantages, prompt-specific baselines, and Difficulty-Aware Prompt Sampling before generation.

## Key Contributions
1. S3AC as an active plug-in on task:token-level-critic-rl.

## Empirical Highlights
Outperforms GRPO-X on dense and MoE models 1.5B-397B. At 35B, single-rollout training holds while tested critic-free baselines deteriorate. Does not retarget method:bpco.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.35518`
- Code: `none found (`code_status: none`).`
