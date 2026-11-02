---
id: paper:no-free-loop
type: paper
title: 'There Is No Free Loop: When Does Looping a Trained Model Pay for Its Inference Compute?'
authors:
- Rhea Sanjay Sukthanker
- Pashmina Cameron
year: 2026
month: 10
arxiv_id: '2610.42030'
url: https://arxiv.org/abs/2610.42030
methods:
- method:elr
- method:uploop
- method:looped-models-done-right
cites:
- paper:elr
- paper:uploop
- paper:looped-models-done-right
tags:
- looped-lm
- gotcha
---

# There Is No Free Loop: When Does Looping a Trained Model Pay for Its Inference Compute?

## Abstract Summary
Adding a loop after pretraining keeps parameter count, disk, memory, and train cost unchanged, but every generated token pays about (N+m)/N times the unlooped cost. Against an equal-parameter unlooped twin and an equal-FLOP unlooped use of the same inference budget, only the looped 0.8B Qwen3/Qwen3.5 model beats both. At 4B and 9B the looped model fails the equal-parameter test even though the unlooped 9B still scores up to 13 points above the 4B, so the benches are not saturated.

## Key Contributions
1. Post-train loops pay only at 0.8B; 4B/9B fail the equal-parameter test.

## Empirical Highlights
Gotcha on method:elr / method:uploop / method:looped-models-done-right. Does not retarget those first hops. Train-time loops (UpLoop, ELR, Huginn) are a different setting.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.42030`
- Code: none found (`code_status: none`).
