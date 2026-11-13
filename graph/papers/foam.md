---
id: paper:foam
type: paper
title: 'Factored One-sided Adam-Moment for Practical and Scalable SOAP'
authors:
- Jaemyung Yu
- Byeongho Heo
- Sangdoo Yun
- Dongyoon Han
year: 2026
month: 11
arxiv_id: '2611.16905'
url: https://arxiv.org/abs/2611.16905
methods:
- method:foam
cites: []
tags:
- optimizer
- soap
- pretraining
- active
---

# Factored One-sided Adam-Moment for Practical and Scalable SOAP

## Abstract Summary
FOAM keeps SOAP's Kronecker-factored curvature on the input Gram only and factors Adam's second moment. NAVER AI Lab. Matches Muon and SOAP validation loss from 124M to 760M while using about half of SOAP's optimizer state. Time-to-AdamW quality $t_A$ within 7% of AdamW; 51% of SOAP wall-clock to SOAP quality. Peak memory +7.4% vs AdamW vs SOAP +12.9%. GitHub `naver-ai/foam` is README-only (`code_status: announced`). Does not retarget Muon2 or KL-SOAP.

## Key Contributions
1. One-sided SOAP: precondition only the input Gram; drop the output-side eigendecomposition.
2. Factored Adam second-moment in the same Kronecker layout so optimizer state stays linear in the SOAP factors.
3. Matches full SOAP / Muon quality at AdamW-like wall-clock on 124M–760M dense pretrain.

## Empirical Highlights
124M–760M dense: FOAM tracks Muon and SOAP val loss. Optimizer state ~50% of SOAP. $t_A$ within 7% of AdamW. 51% of SOAP wall-clock to SOAP quality. Peak mem +7.4% vs AdamW (SOAP +12.9%). Distinct from Clean (Nyström SOAP sketch) and KL-SOAP (full second-order hop).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.16905`
- Code: `https://github.com/naver-ai/foam` (`code_status: announced`; README-only as of 2026-11-13).
