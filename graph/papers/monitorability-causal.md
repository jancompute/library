---
id: paper:monitorability-causal
type: paper
title: 'Learning to Be Monitored: Causal Bounds and Intervention-Aware Post-Training Recipes for Chain-of-Thought Monitorability'
authors:
- 'Qiang Fu'
- 'Xinyue Li'
- 'Andre Wibisono'
- 'Arman Cohan'
year: 2026
month: 10
arxiv_id: '2610.31733'
url: https://arxiv.org/abs/2610.31733
methods:
- method:cispo
- method:monitorability-trainable
cites:
- paper:minimax-m1
- paper:monitorability-trainable
tags:
- rlvr
- gotcha
- monitorability
---

# Learning to Be Monitored

## Abstract Summary
CoT monitorability evals that use interventions need causal bounds. Minimal-criterion TPR can overstate detectability; intervention-aware post-training is a recipe, not a Pass@1 loss.

## Key Contributions
1. Causal bounds for CoT monitorability; not a CISPO replacement.

## Empirical Highlights
- Does not retarget CISPO. Pair with method:monitorability-trainable.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.31733`
- Code: `none found` (`code_status: none`).
