---
id: paper:opd-token-order
type: paper
title: 'Which Tokens, in What Order, and How Fast? A Theoretical Analysis of On-Policy Distillation Objectives'
authors:
- Hubert Strauss
- Liam Fowl
- Noam Razin
year: 2026
month: 11
arxiv_id: '2611.23397'
url: https://arxiv.org/abs/2611.23397
methods:
- method:opd
cites: []
tags:
- opd
- theory
- reverse-kl
- claim-note
---

# Which Tokens, in What Order, and How Fast?

## Abstract Summary
Claim note on `method:opd`, not a trainer. Sequence-level OPD has a future-agreement bias; reverse-KL OPD can vanish. Qwen3-1.7B student vs Qwen3-8B teacher: sequence-level OPD refuses nearly all WildJailbreak benign requests (teacher 17.5%). Code princeton-pli/opd-objectives-analysis. Does not retarget OPD.

## Key Contributions
1. Sequence-level future-agreement bias in OPD objectives.
2. Reverse-KL vanishing-gradient analysis.
3. Safety transfer gotcha: sequence-level OPD over-refuses relative to the teacher.

## Empirical Highlights
Qwen3-1.7B vs Qwen3-8B: sequence-level OPD refuses nearly all WildJailbreak benign requests (teacher 17.5%).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.23397`
- Code: `https://github.com/princeton-pli/opd-objectives-analysis`
