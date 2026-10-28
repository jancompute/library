---
id: paper:muongs
type: paper
title: 'MuonGS: Pretraining LLMs with Relaxed Weight-Norm Control'
authors:
- 'Athanasios Glentis'
- 'Dawei Li'
- 'Mingyi Hong'
year: 2026
month: 10
arxiv_id: '2610.37647'
url: https://arxiv.org/abs/2610.37647
methods:
- method:muongs
cites:
- paper:muon2
tags:
- optimizer
- muon
- active
---

# MuonGS: Pretraining LLMs with Relaxed Weight-Norm Control

## Abstract Summary
Weight-norm control in Muon is analyzed via accumulated effective learning rate. Vanilla Muon can accumulate only logarithmically. MuonGS removes the radial component of each update without fixing the weight norm and proves C_T = Omega(sqrt(T)).

## Key Contributions
1. MuonGS as an active Muon-family plug-in on task:llm-pretraining-optimization.

## Empirical Highlights
Lower validation perplexity than MuonH at long horizon; dense token-equivalent speedup up to about 15%. Does not retarget method:muon2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37647`
- Code: `none found (`code_status: none`).`
