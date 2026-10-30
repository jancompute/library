---
id: paper:opd-entropy-shape
type: paper
title: 'Distilling the Shape of Uncertainty: What On-Policy Distillation Learns and How to Predict It'
authors:
- 'Shiping Yang'
- 'Chuanqi Tang'
- 'Hossein Hajimirsadeghi'
- 'Layla El Asri'
- 'Mohammad Amin Shabani'
- 'Angel X. Chang'
year: 2026
month: 10
arxiv_id: '2610.39020'
url: https://arxiv.org/abs/2610.39020
methods:
- method:opd
cites:
- paper:opd
tags:
- opd
- gotcha
---

# Distilling the Shape of Uncertainty: What On-Policy Distillation Learns and How to Predict It

## Abstract Summary
OPD learns both which tokens to consider and where to keep paths open. Entropy shape (the sequence of next-token entropies) plus ESC (entropy-shape correlation) predicts teacher quality. Intervening on teacher entropy while freezing token preferences shows where-to-branch causally drives OPD gains. Code maybenotime/opd-esc.

## Key Contributions
1. ESC teacher-selection protocol for OPD; not an OPD replacement.

## Empirical Highlights
Pre-OPD ESC picks the best teacher for both students vs existing predictors. Does not retarget method:opd.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.39020`
- Code: `https://github.com/maybenotime/opd-esc (`code_status: released`).`
