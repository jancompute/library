---
id: paper:bac-mopd
type: paper
title: 'Branch and Consolidate: A Unified Recipe for Multi-Teacher On-Policy Distillation'
authors:
- Zihan Liang
- Zikun Qu
- Ben Chen
- Fan Yang
- Wenwu Ou
- Min Zhang
- Zhongxiang Dai
- Xinchao Wang
year: 2026
month: 11
arxiv_id: '2611.32515'
url: https://arxiv.org/abs/2611.32515
methods:
- method:bac-mopd
cites: []
tags:
- distillation
- mopd
- consolidation
---

# Branch and Consolidate: A Unified Recipe for Multi-Teacher On-Policy Distillation

## Abstract Summary
Independently post-trained specialists drift so far from a shared checkpoint that vanilla MOPD cannot recover them. BaC-MOPD merge-inits the student, distills on error-replay queries, averages reverse-KL first per teacher then equally across teachers, and anchors with a frozen copy of the merged init. Paper IM-MOPD numbers are not the library 83.4% bake-off.

## Key Contributions
1. Merge as MOPD init rather than as the final model.
2. Error-replay queries plus a frozen self-teacher on the merge init.
3. Per-teacher then equal-across-teachers reverse-KL.

## Empirical Highlights
Industrial six-specialist recovery 97.0% vs IM-MOPD 79.8% vs best merge 42.3%. Open Qwen3-4B 95.7% after consolidation / 97.5% after refinement vs IM-MOPD 94.1%.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.32515`
- Code: announced, not released as of 2026-11-25
