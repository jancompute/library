---
id: paper:ghc
type: paper
title: 'GHC: Expanding Residual Interfaces in Hyper-Connections'
authors:
- Tianyu Li
- Hongtao Zhang
- Dongchen Han
- Jingshu Liu
- Bojun Wang
- Chen Jiang
- Yulong Huang
- Wei Chen
- Tianyu He
- Xiangyu Zhang
- Gao Huang
year: 2026
month: 11
arxiv_id: '2611.31350'
url: https://arxiv.org/abs/2611.31350
methods:
- method:ghc
cites: []
tags:
- architecture
- hyper-connections
- pretraining
- moe
---

# GHC: Expanding Residual Interfaces in Hyper-Connections

## Abstract Summary
Hyper-Connections keep a narrow residual interface. GHC partitions each branch into groups; each group reads its own stream mix and writes a distinct output. Default \(n=4\), \(r=8\), TanhSiLU, freeze first-layer \(H_{\mathrm{pre}}\). Distinct from mHC, SimpleHC, TPHC, cmHC.

## Key Contributions
1. Grouped residual read/write instead of a single \(c\)-dimensional mix.
2. Signed TanhSiLU group scaling plus frozen first-layer \(H_{\mathrm{pre}}\).
3. 430M dense and 4B/13B MoE pretrain vs IHC and Pre-Norm.

## Empirical Highlights
430M dense val loss 2.0161 vs IHC 2.0351 / Pre-Norm 2.0713; Avg. Score 25.80. Train efficiency +35% vs Pre-Norm, +10% vs IHC. 13BA0.6B MoE 1.6775 / 43.96 vs IHC 1.6901 / 42.59. Extra streams help GHC (−0.0195) but not IHC (−0.0028).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.31350`
- Code: none found as of 2026-11-25
