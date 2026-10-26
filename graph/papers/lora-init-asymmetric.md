---
id: paper:lora-init-asymmetric
type: paper
title: 'Rethinking LoRA Initialization for Robust Asymmetric Learning Rates'
authors:
- 'Disen Liao'
- 'Yaoliang Yu'
year: 2026
month: 10
arxiv_id: '2610.32142'
url: https://arxiv.org/abs/2610.32142
methods:
- method:lora-init-asymmetric
cites:
- paper:lr-matters-lora
tags:
- peft
- lora
- active
---

# Rethinking LoRA Initialization for Robust Asymmetric Learning Rates

## Abstract Summary
LoRA is LR-sensitive; after a sweep vanilla LoRA stays competitive. This paper re-inits LoRA so LoRA+ asymmetric LRs are less brittle.

## Key Contributions
1. LoRA init-asymmetric as an active plug-in on task:lora-quality-tuning.

## Empirical Highlights
- Init that stabilizes LoRA+ asymmetric LRs. Does not supersede vanilla LoRA + rsLoRA + LR sweep.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.32142`
- Code: `none found` (`code_status: none`).
