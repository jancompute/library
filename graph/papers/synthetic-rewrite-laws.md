---
id: paper:synthetic-rewrite-laws
type: paper
title: 'Rewriting Scaling Laws for Synthetic Data with Compute and Data Constraints'
authors:
- 'Nicholas Roberts'
- 'Ahmed Ahmed'
- 'Suhas Kotha'
- 'Percy Liang'
- 'Yu Wang'
- 'Alex Renda'
- 'Nitya Mani'
year: 2026
month: 10
arxiv_id: '2610.31867'
url: https://arxiv.org/abs/2610.31867
methods:
- method:olmo-3
- method:synth
cites:
- paper:olmo-3
- paper:synth
tags:
- data-curriculum
- gotcha
- synthetic
---

# Rewriting Scaling Laws for Synthetic Data with Compute and Data Constraints

## Abstract Summary
Synthetic rewrites are a standard pretrain ingredient. This paper asks how much compute to spend rewriting and whether a student trained on rewrites can beat the rewriter.

## Key Contributions
1. Rewrite scaling under compute/data constraints; not a mix default.

## Empirical Highlights
- Does not retarget OLMo-3 or SYNTH. Rewrite spend is a budgeted axis, not a free quality knob.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.31867`
- Code: `none found` (`code_status: none`).
