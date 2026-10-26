---
id: paper:looped-halting-heads
type: paper
title: 'Do Halting Heads Really Save Compute in Looped Language Models?'
authors:
- 'Tsung-Han Wu'
- 'Minsuk Heo'
- 'Kenny Tan'
year: 2026
month: 10
arxiv_id: '2610.32246'
url: https://arxiv.org/abs/2610.32246
methods:
- method:looped-models-done-right
cites:
- paper:looped-models-done-right
tags:
- architecture
- gotcha
- looped
---

# Do Halting Heads Really Save Compute in Looped Language Models?

## Abstract Summary
Halting heads that mix all iterations do not save compute as advertised. Pretrain up to 1.3B shows the head trained on mixed iterations predicts poorly for early exit.

## Key Contributions
1. Halting-head compute-save gotcha; not a looped-LM default.

## Empirical Highlights
- Does not retarget RLT or Looped Models Done Right. Mixed-iteration halt labels are the failure mode.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.32246`
- Code: `none found` (`code_status: none`).
