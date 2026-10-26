---
id: paper:gift
type: paper
title: 'GIFT: Gradient Informed Filtering for Distillation Augmented Reasoning RL'
authors:
- 'Shijie Li'
- 'Yilin Gao'
- 'Tieyuan Chen'
- 'Yun Luo'
- 'Weiyao Lin'
- 'Hang Yu'
year: 2026
month: 10
arxiv_id: '2610.30796'
url: https://arxiv.org/abs/2610.30796
methods:
- method:gift
cites:
- paper:opd
- paper:minimax-m1
tags:
- distillation
- rlvr
- active
---

# GIFT

## Abstract Summary
Training reasoning models mixes sparse outcome RL with dense token-level distillation, but complementarity of supervision does not imply compatibility of gradients. GIFT filters distillation tokens by whether their gradient agrees with the RL objective.

## Key Contributions
1. GIFT as an active plug-in on task:student-distillation.

## Empirical Highlights
- Filters imitation tokens that conflict with outcome RL. Does not retarget method:opd or method:cispo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.30796`
- Code: `https://github.com/lilifree/GIFT` (`code_status: released`).
