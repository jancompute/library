---
id: paper:looped-depth-reusable
type: paper
title: 'Agreement rather than normalisation keeps depth reusable in looped language models'
authors:
- 'Ivan Viakhirev'
- 'Kirill Borodin'
- 'Maxim Abramov'
- 'Grach Mkrtchian'
year: 2026
month: 10
arxiv_id: '2610.31943'
url: https://arxiv.org/abs/2610.31943
methods:
- method:looped-models-done-right
cites:
- paper:looped-models-done-right
tags:
- architecture
- gotcha
- looped
---

# Agreement rather than normalisation keeps depth reusable in looped language models

## Abstract Summary
Looped LMs pay off only if extra inference loops stay usable. On released Ouro weights, train/run loop agreement matters more than normalizing the state between loops.

## Key Contributions
1. Depth-reuse gotcha for looped LMs; not a new architecture default.

## Empirical Highlights
- Does not retarget RLT or Looped Models Done Right. Match train and run loop counts.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.31943`
- Code: `none found` (`code_status: none`).
