---
id: paper:flamia
type: paper
title: 'FLAMIA: FLAsh MIcroscaling Attention for Fast and Causally Safe Training on Blackwell'
authors:
- 'Fedor Velikonivtsev'
- 'Mikhail Koltakov'
- 'Denis Kuznedelev'
year: 2026
month: 11
arxiv_id: '2611.03344'
url: https://arxiv.org/abs/2611.03344
methods:
- method:flamia
cites:
- paper:quartet-ii
- paper:mxfp4-mi355x
tags:
- fp4
- attention
- blackwell
- active
---

# FLAMIA: FLAsh MIcroscaling Attention for Fast and Causally Safe Training on Blackwell

## Abstract Summary
Blackwell low-precision GEMM needs attention kernels that avoid quantization overhead, causal leakage through shared scales, and forward/backward numeric drift. FLAMIA is MXFP8 and mixed NVFP4/FP8 attention with token-block scaling, leakage safeguards, fused quantization, and packed-document scheduling.

## Key Contributions
1. Causally safe MXFP8 / NVFP4 attention training kernels for Blackwell.

## Empirical Highlights
Combined fwd+bwd attention including quantization 1.10-1.40x on B200 and 1.06-1.42x on B300 vs the fastest evaluated baseline per workload. Llama-style pretrain quality preserved. Code yandex-research/flamia-blackwell-attention.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03344`
- Code: `https://github.com/yandex-research/flamia-blackwell-attention` (`code_status: released`).
