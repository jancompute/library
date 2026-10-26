---
id: paper:op-self-training
type: paper
title: 'On-Policy Self-Training: Data-Free Self-Improvement in Large Language Models'
authors:
- 'Leon Sick'
- 'Lukas Hoyer'
- 'Yannick Strümpler'
- 'Christian Reisswig'
- 'Timo Ropinski'
- 'Federico Tombari'
year: 2026
month: 10
arxiv_id: '2610.32770'
url: https://arxiv.org/abs/2610.32770
methods:
- method:op-self-training
cites:
- paper:j-zero
- paper:opd
tags:
- self-distillation
- data-free
- active
---

# On-Policy Self-Training

## Abstract Summary
On-policy self-distillation usually still needs labeled QA. This paper self-generates the pairs and privileged reasoning so the loop is data-free.

## Key Contributions
1. On-policy self-training as an active plug-in on task:data-free-self-evolution.

## Empirical Highlights
- Self-generated QA self-distill. Does not retarget method:j-zero.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.32770`
- Code: `none found` (`code_status: none`).
