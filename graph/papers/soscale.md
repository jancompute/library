---
id: paper:soscale
type: paper
title: 'SoScale: Second-Order Scale Search for FP4 Quantization'
authors:
- Pengxiang Zhao
- Xing Li
- Hui-Ling Zhen
- Weizhe Lin
- Xianzhi Yu
- Zhenhua Dong
year: 2026
month: 11
arxiv_id: '2611.16426'
url: https://arxiv.org/abs/2611.16426
methods:
- method:soscale
cites: []
tags:
- quantization
- fp4
- ptq
- active
---

# SoScale: Second-Order Scale Search for FP4 Quantization

## Abstract Summary
Hessian-aware hierarchical FP4 scale-code search plus GPTQ recovery for W4A4. Qwen3-14B retains 97.17% / 99.20% / 99.40% of BF16 average under MXFP4 / NVFP4 / HiF4. +0.21–0.77 vs strongest non-SoScale; +0.47–1.10 vs local ScaleSearch. Distinct from DualQuant / ResCom / native Quartet-II training. No public code. Does not retarget Quartet-II.

## Key Contributions
1. Second-order (Hessian-aware) search over hierarchical FP4 scale codes instead of max-abs default scaling.
2. GPTQ recovery after the scale assignment.
3. Same search on MXFP4, NVFP4, and HiF4 payloads.

## Empirical Highlights
Qwen3-14B W4A4 retains 97.17%/99.20%/99.40% of BF16 avg under MXFP4/NVFP4/HiF4. +0.21–0.77 vs strongest non-SoScale; +0.47–1.10 vs local ScaleSearch.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.16426`
- Code: none found (`code_status: none`).
