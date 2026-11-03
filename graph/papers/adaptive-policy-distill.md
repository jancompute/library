---
id: paper:adaptive-policy-distill
type: paper
title: 'Adaptive-Policy Distillation: Knowledge Injection under Information Asymmetry'
authors:
- 'Hojun Cho'
- 'Kang Eun Jeon'
- 'Jaegul Choo'
year: 2026
month: 11
arxiv_id: '2611.00852'
url: https://arxiv.org/abs/2611.00852
methods:
- method:adaptive-policy-distill
cites:
- paper:opd
tags:
- opd
- knowledge-injection
- active
---

# Adaptive-Policy Distillation: Knowledge Injection under Information Asymmetry

## Abstract Summary
Reverse-KL OPD injects document knowledge far less efficiently than off-policy distillation: student-weighted reverse KL barely lifts unlikely document tokens, and later target positions stay unexposed until prefixes are correct. Adaptive-Policy Distillation (APD) gates per token toward the teacher and toward forward KL where needed, then withdraws both as the student learns. No labels or verifier.

## Key Contributions
1. Per-token gate that shifts rollout toward the teacher and the objective toward forward KL for knowledge injection.

## Empirical Highlights
Up to +54.6% vs OPD; QASPER 0.558 F1 and BioASQ 0.486 MRR, best in the paper.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.00852`
- Code: none found (`code_status: none`).
