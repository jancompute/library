---
id: paper:gga-pw
type: paper
title: 'Low-Bit GDN Recurrent-State Quantization: Global Gradient-aware Allocation and Pure-Write Sliding Windows'
authors:
- 'Qinghang Huang'
- 'Xuchu Huang'
- 'Xunzhao Yin'
year: 2026
month: 10
arxiv_id: '2610.39931'
url: https://arxiv.org/abs/2610.39931
methods:
- method:gga-pw
cites:
- paper:pace
tags:
- gdn
- quantization
- active
---

# Low-Bit GDN Recurrent-State Quantization: Global Gradient-aware Allocation and Pure-Write Sliding Windows

## Abstract Summary
GGA allocates mixed head bit-widths from quantization residuals times gradient sensitivity under a global budget. PW keeps recent writes as FP8 pairs, runs them through the full GDN transition, and merges into the low-bit history so recency is not rounded away.

## Key Contributions
1. Mixed-precision GDN state quant plus a pure-write recency window; PACE sibling.

## Empirical Highlights
Cuts long-reasoning degradation / repetition from quantized writeback. No public code. Does not retarget method:mamba-2 or method:pace.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.39931`
- Code: `none found (`code_status: none`).`
