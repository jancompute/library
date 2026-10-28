---
id: paper:delta-learning-limits
type: paper
title: 'Exploring the Limits of the Delta Learning Hypothesis: Single-Pair Generator Biases in Direct Preference Optimization'
authors:
- 'Giuseppe Curci'
- 'Stefano Simonazzi'
- 'Andrea Molinari'
- 'Andrea Zugarini'
year: 2026
month: 10
arxiv_id: '2610.37058'
url: https://arxiv.org/abs/2610.37058
methods:
- method:olmo-3
cites:
- paper:olmo-3
tags:
- preference-alignment
- gotcha
- dpo
---

# Exploring the Limits of the Delta Learning Hypothesis: Single-Pair Generator Biases in Direct Preference Optimization

## Abstract Summary
Delta learning from a single larger/smaller generator pair injects generator-dependent biases that predict the preference label independent of response quality. DPO on that data underperforms multi-model pools and shows reward-hacking dynamics.

## Key Contributions
1. Single-pair delta-learning gotcha on task:direct-preference-alignment; not an OLMo-3 replacement.

## Empirical Highlights
Fixed model pairs underperform diverse preference pools even when the larger generator is better. Does not retarget method:olmo-3.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37058`
- Code: `none found (`code_status: none`).`
