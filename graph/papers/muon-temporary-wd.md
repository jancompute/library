---
id: paper:muon-temporary-wd
type: paper
title: 'Delayed Effects of Temporary Weight Decay in Muon Pretraining'
authors:
- Md Rifat Arefin
- Ravid Shwartz-Ziv
- Ernie Chang
- Chinnadhurai Sankar
- Rylan Conway
- Aristide Baratin
- Irina Rish
- Adithya Sagar
- Patrick Huber
year: 2026
month: 11
arxiv_id: '2611.17876'
url: https://arxiv.org/abs/2611.17876
methods:
- method:muon2
cites: []
tags:
- muon
- weight-decay
- gotcha
- active
---

# Delayed Effects of Temporary Weight Decay in Muon Pretraining

## Abstract Summary
Claim note, no trainer. A temporary Muon weight-decay window can look worse at removal and still finish better. 1.4B FineWeb-100B: λ=0.15 for the first 44% is 0.26 nats worse at removal, overtakes at 73%, finishes 0.0275–0.028 nats better than no decay (also beats the best constant decay). Early vs late windows reverse sign (late from 60% hurts). Evaluate at the intended final budget, not at removal. Link `method:muon2`. Complements `paper:muon-sw-tuning-gap`. No public code. Does not retarget Muon2.

## Key Contributions
1. Temporary WD quality at removal is not the quality at the intended budget.
2. Early window can finish better than no decay and better than the best constant decay.
3. Late window (from 60%) reverses the sign.

## Empirical Highlights
1.4B FineWeb-100B: 0.26 nats worse at removal, overtakes at 73%, finishes 0.0275–0.028 nats better than no decay.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.17876`
- Code: none found.
