---
id: paper:budget-internalization
type: paper
title: 'Budget Internalization: Fixed-Budget RLVR Trades Test-Time Scaling for In-Budget Accuracy'
authors:
- Ilia Zavidnyi
- Alexander Kovrigin
- Arina Puchkova
- Kirill Gelvan
- Sergey Titov
year: 2026
month: 11
arxiv_id: '2611.26172'
url: https://arxiv.org/abs/2611.26172
methods:
- method:cispo
cites: []
tags:
- rlvr
- length
- budget
- cispo
---

# Budget Internalization: Fixed-Budget RLVR Trades Test-Time Scaling for In-Budget Accuracy

## Abstract Summary
Claim note, no new method. Training under a generation budget internalizes that budget: Qwen3.5-4B gains +34.8pp at 4k and loses −30.2pp at 64k. SFT on truncated traces reproduces the same pattern. Complements When2Think / LoCo / AES / LSD / `paper:two-clocks-rlvr`. Checkpoints at huggingface.co/collections/JetBrains-Research/budget-internalization.

## Key Contributions
1. Budget internalization is not unique to RLVR; truncated SFT is enough.
2. Short-budget gains reverse at long eval.
3. Release of 4B checkpoints for the length-transfer grid.

## Empirical Highlights
Qwen3.5-4B 4k +34.8pp / 64k −30.2pp vs the unrestricted train budget.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.26172`
- Checkpoints: `https://huggingface.co/collections/JetBrains-Research/budget-internalization`
