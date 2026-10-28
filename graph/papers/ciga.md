---
id: paper:ciga
type: paper
title: 'Robust LLM Data Selection via Content-Invariant Gradient Attribution'
authors:
- 'Jia Gu'
- 'Liang Pang'
- 'Huawei Shen'
year: 2026
month: 10
arxiv_id: '2610.36755'
url: https://arxiv.org/abs/2610.36755
methods:
- method:ciga
cites:
- paper:magic
tags:
- data-attribution
- active
---

# Robust LLM Data Selection via Content-Invariant Gradient Attribution

## Abstract Summary
Global gradient attribution is biased by wording and format. CIGA keeps layers that are influential and stable under semantics-preserving perturbations, then fuses those features for instruction-data selection.

## Key Contributions
1. CIGA as an active surface-form-robust selection plug-in on task:training-data-attribution.

## Empirical Highlights
Reduces surface-form flip of attribution scores for instruction data. Does not retarget method:magic.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36755`
- Code: `none found (`code_status: none`).`
