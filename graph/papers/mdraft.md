---
id: paper:mdraft
type: paper
title: 'Multi-Draft On-Policy Distillation for Diffusion Drafters'
authors:
- 'Petr Molodyk'
- 'Yuchen Zhu'
- 'Jaemoo Choi'
- 'Molei Tao'
- 'Yongxin Chen'
year: 2026
month: 10
arxiv_id: '2610.37778'
url: https://arxiv.org/abs/2610.37778
methods:
- method:mdraft
cites:
- paper:uno
tags:
- speculative-decoding
- opd
- active
---

# Multi-Draft On-Policy Distillation for Diffusion Drafters

## Abstract Summary
One-step diffusion drafters predict a block without seeing in-block prefixes, while the verifier conditions on those prefixes, so separate OPD targets can suppress tokens that are good after some prefixes. MDraft samples several draft blocks from the same context and aggregates the verifier's full-vocab conditionals across prefixes.

## Key Contributions
1. Multi-draft aggregation for on-policy distillation of parallel diffusion drafters.

## Empirical Highlights
Avoids prefix-mismatch suppression of acceptable tokens. No public code. Does not retarget method:uno.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37778`
- Code: `none found (`code_status: none`).`
