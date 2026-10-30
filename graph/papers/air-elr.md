---
id: paper:air-elr
type: paper
title: 'Your LR Schedule May Not Be Principled: Effective Learning Rate Scheduling in Weight-Normalized Training'
authors:
- 'Qifan Yu'
- 'Xinyu Ma'
- 'Xingyan Bin'
- 'Di He'
year: 2026
month: 10
arxiv_id: '2610.40362'
url: https://arxiv.org/abs/2610.40362
methods:
- method:air-elr
cites:
- paper:muon2
tags:
- optimizer
- lr-schedule
- active
---

# Your LR Schedule May Not Be Principled: Effective Learning Rate Scheduling in Weight-Normalized Training

## Abstract Summary
Weight-normalized training gains vs weight decay are driven mostly by the induced effective learning rate trajectory. Matching ELR collapses WN and WD loss dynamics. AIR combines a 1/sqrt(t) decay with an affine map so peak and terminal LRs fit a finite horizon; late-stage ELR dominates earlier schedule choices.

## Key Contributions
1. AIR affine 1/sqrt(t) ELR schedule as an active pretrain LR plug-in on task:llm-pretraining-optimization.

## Empirical Highlights
128B-token MoE runs; ~0.01 loss vs cosine at matched peak/terminal LR. Does not retarget method:muon2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.40362`
- Code: `none found (`code_status: none`).`
