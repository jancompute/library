---
id: paper:hinted-scaling-laws
type: paper
title: 'Hinted Scaling Laws'
authors:
- 'Suze van Adrichem'
- 'Luke Bailey'
- 'Rohith Kuditipudi'
- 'Christine Ye'
- 'Neil Band'
- 'Ahmed Ahmed'
- 'John Duchi'
- 'Percy Liang'
- 'Tatsunori Hashimoto'
year: 2026
month: 11
arxiv_id: '2611.02270'
url: https://arxiv.org/abs/2611.02270
methods:
- method:muon2
cites:
- paper:muon2
- paper:olmo-3
tags:
- scaling
- gotcha
---

# Hinted Scaling Laws

## Abstract Summary
Downstream accuracy scaling laws fail when small models score near zero. Hinted scaling laws turn a bench into a continuum of easier versions so small models score above zero. On Delphi, a fit at <=10^20 FLOPs forecasts 10^23 GSM8K (25.9%) within 3pp; a standard law under-forecasts by 13pp on the same models and by 12pp even with fits to 10^22. Median GSM8K/AIME/HLE error 21pp to 4.3.

## Key Contributions
1. Privileged hints make small-model accuracy a usable scaling-law signal.

## Empirical Highlights
Gotcha / tool on task:llm-pretraining-optimization. Does not retarget Muon2 or OLMo-3.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02270`
- Code: none found (`code_status: none`).
