---
id: paper:c-grpo
type: paper
title: 'C-GRPO: Conformal Group Relative Policy Optimization'
authors:
- Arya Fayyazi
- Seyedarmin Azizi
- Mehdi Kamal
- Massoud Pedram
year: 2026
month: 11
arxiv_id: '2611.05591'
url: https://arxiv.org/abs/2611.05591
methods:
- method:c-grpo
cites:
- paper:minimax-m1
- paper:ngu
- paper:adaroll-grpo
- paper:thinkprior
tags:
- rlvr
- conformal
- neurips-2026
- active
---

# C-GRPO: Conformal Group Relative Policy Optimization

## Abstract Summary
C-GRPO replaces GRPO's fixed rollout budget with calibrated conformal thresholds. APS-style sets cover closed-form answers; a first-success score covers execution-based code. Finite-sample false-stop control holds at every budget. Distinct from citation-aware C-GRPO.

## Key Contributions
1. Split-conformal adaptive group size with automatic miscoverage and periodic recalibration.
2. 49–70% fewer training rollouts vs G=32 GRPO at matched pass@1; up to 82% savings on Llama-3.1-8B GSM8K.

## Empirical Highlights
NeurIPS 2026. Accuracy deltas sit in binomial noise. Sibling of NGU / ThinkPrior / AdaRoll-GRPO. Does not retarget CISPO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.05591`
- Code: `https://github.com/AryaFayyazi/CGRPO` (`code_status: released`); `pip install trl-cgrpo`.
