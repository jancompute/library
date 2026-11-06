---
id: paper:o2pd
type: paper
title: 'O2PD: Overlap-Gated Prefix Distillation'
authors:
- Shuaishuai Zu
- Jihao Zhao
- Pengfei Li
- Guanghuan Fang
- Ben Feng
- Yuhan Liu
- Biao Qin
- Baochuan Yang
year: 2026
month: 11
arxiv_id: '2611.07731'
url: https://arxiv.org/abs/2611.07731
methods:
- method:o2pd
cites:
- paper:opd
- paper:sparse-opd-supervision
tags:
- distillation
- opd
- active
---

# O2PD: Overlap-Gated Prefix Distillation

## Abstract Summary
O²PD distills only the first 20% of each student trajectory, mixes forward and reverse KL with an overlap-gated $\alpha$-divergence, and adds a reset atom plus support-convergence term. VERL, $k=16$, DAPO-MATH-17K. No public code as of 2026-11-06.

## Key Contributions
1. Fixed prefix fraction instead of entropy / usefulness keep-masks.
2. Overlap-gated $\alpha$-divergence switches covering (FKL) vs mode-seeking (RKL) with teacher–student support overlap.
3. Seven-suite Avg vs OPD: $+1.89$ / $+4.81$ / $+5.29$ on Qwen3-1.7B←4B ($26.80$), DSR1-1.5B←JustRL-1.5B ($39.48$), 1.7B←4B-NTRL ($50.58$ vs OPD $45.29$).

## Empirical Highlights
Table 2. Prefix selection beats ESR / EOPD / TIP on Avg for all three pairs. Does not retarget OPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.07731`
- Code: none found (`code_status: none`). Host trainer: VERL.
