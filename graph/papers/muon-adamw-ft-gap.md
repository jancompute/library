---
id: paper:muon-adamw-ft-gap
type: paper
title: 'Pretraining Data Scale Reverses the Muon-AdamW Fine-Tuning Gap'
authors:
- 'Catherine Li'
- 'Jingchu Gai'
- 'Andrej Risteski'
- 'Jacob Mitchell Springer'
- 'Aditi Raghunathan'
year: 2026
month: 11
arxiv_id: '2611.03633'
url: https://arxiv.org/abs/2611.03633
methods:
- method:muon2
cites:
- paper:muon2
tags:
- muon
- gotcha
---

# Pretraining Data Scale Reverses the Muon-AdamW Fine-Tuning Gap

## Abstract Summary
Muon wins pretrain loss, but after a large enough pretrain data budget AdamW outperforms Muon after fine-tuning. As model size grows, AdamW overtakes at smaller token-parameter ratios. The paper's margin-to-spread ratio tracks the reversal; a linear associative-memory proof shows gradient descent's ratio gaining on Muon as data grows.

## Key Contributions
1. Pretrain-data scale can reverse Muon's fine-tune advantage versus AdamW.

## Empirical Highlights
Gotcha on method:muon2. Does not retarget Muon2 for from-scratch pretrain.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03633`
- Code: none found (`code_status: none`).
