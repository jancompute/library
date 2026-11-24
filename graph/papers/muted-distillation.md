---
id: paper:muted-distillation
type: paper
title: 'Muted Distillation: Sealing Reasoning from Teacher Unlocks Token-Efficient Agents'
authors:
- Yuwei Zhang
- Ian Miao
- Wentao Zhang
- Chen Qu
- Bill Bi
- Jingbo Shang
- Donna Schut
year: 2026
month: 11
arxiv_id: '2611.28445'
url: https://arxiv.org/abs/2611.28445
methods:
- method:muted-distillation
cites: []
tags:
- distillation
- opd
- token-efficiency
- agents
---

# Muted Distillation: Sealing Reasoning from Teacher Unlocks Token-Efficient Agents

## Abstract Summary
Muted Distillation hides the student's thought tokens from the OPD teacher and applies reverse-KL only on the visible tail. Standard OPD inflates per-turn reasoning because the teacher extends partial thoughts. No extra data or hyperparameters. No public code.

## Key Contributions
1. Teacher-context mute: replace student thoughts with an empty thinking block.
2. Loss on tail tokens only, so thought padding cannot dominate the gradient.
3. OfficeQA Pro / SpreadsheetBench token cuts vs OPD at matched or better accuracy.

## Empirical Highlights
OfficeQA Pro / SpreadsheetBench output tokens per episode −57% / −53% vs OPD. SpreadsheetBench pass@1 +4.8 vs OPD. Student becomes more concise than the untrained base. Qwen3.5 4B/9B/27B.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.28445`
- Code: none found as of 2026-11-24
