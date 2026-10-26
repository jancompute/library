---
id: paper:cyclegrpo
type: paper
title: 'Generalized CycleGRPO for Fine-Grained Multimodal Understanding and Grounding'
authors:
- 'Xin Zhang'
- 'Haochen Wang'
- 'Beibei Lin'
- 'Zhaoxiang Zhang'
- 'Robby T. Tan'
- 'Jason Li'
- 'Dacheng Tao'
year: 2026
month: 10
arxiv_id: '2610.29552'
url: https://arxiv.org/abs/2610.29552
methods:
- method:cyclegrpo
cites:
- paper:vision-rl2
tags:
- multimodal-rl
- grounding
- active
---

# Generalized CycleGRPO for Fine-Grained Multimodal Understanding and Grounding

## Abstract Summary
Fine-grained multimodal models usually split understand vs localize. Generalized CycleGRPO trains both in one RL loop across spatial and temporal domains.

## Key Contributions
1. CycleGRPO as an active plug-in on task:mllm-finegrained-perception-rl.

## Empirical Highlights
- Coupled understand+localize GRPO. Does not retarget method:vision-rl2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.29552`
- Code: `https://github.com/devinxzhang/CycleGRPO` (`code_status: released`).
