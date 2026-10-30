---
id: paper:quantization-loss-spikes
type: paper
title: 'The Role of Quantization in Loss Spikes'
authors:
- 'Zaiqian Chen'
- 'Aditya Somasundaram'
- 'Sophie Li'
- 'Sean McLeish'
- 'John Kirchenbauer'
- 'Tom Goldstein'
- 'Micah Goldblum'
year: 2026
month: 10
arxiv_id: '2610.38277'
url: https://arxiv.org/abs/2610.38277
methods:
- method:muon2
cites:
- paper:muon2
tags:
- optimizer
- quantization
- gotcha
---

# The Role of Quantization in Loss Spikes

## Abstract Summary
Time-bomb loss spikes follow rapidly growing LM-head quantization error. Lower precision accelerates them; higher precision delays them. Replacing AdamW on the LM head with SGD+momentum suppresses logit growth over long horizons.

## Key Contributions
1. LM-head quantization time-bomb plus SGD-momentum-on-head mitigation.

## Empirical Highlights
Does not retarget Muon2. Complements method:energycal (MoE Muon spikes, different layer).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.38277`
- Code: `none found (`code_status: none`).`
