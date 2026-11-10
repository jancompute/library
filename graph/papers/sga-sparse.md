---
id: paper:sga-sparse
type: paper
title: 'SGA-Sparse: Training Native SwiGLU Gates for Activation-Sparse and Low-Bit LLMs'
authors:
- Ruokai Yin
- Steven Li
year: 2026
month: 11
arxiv_id: '2611.11223'
url: https://arxiv.org/abs/2611.11223
methods:
- method:sga-sparse
cites: []
tags:
- sparsity
- swiglu
- quantization
- active
---

# SGA-Sparse

## Abstract Summary
SGA trains the native SwiGLU gate as a top-$k$ FFN router. $75$–$85\%$ FFN sparsity, $0.2$–$2.7$pp of dense, $\sim 30$B tokens, LLaMA $1$B–$8$B. PTQ of the sparse model degrades; continued-QAT / joint-QAT recover. $2.5$-bit-eq matches dense $3$-bit QAT; $1.5$-bit-eq beats ternary $+1.3$pp. No public code as of 2026-11-10. Does not replace GradCodeS.

## Key Contributions
1. Reuse the SwiGLU gate as the sparse router instead of adding a separate MoE router.
2. Joint / continued QAT for the sparse checkpoint (plain PTQ fails).
3. Bit-equivalent comparisons vs dense QAT and ternary.

## Empirical Highlights
$75$–$85\%$ FFN sparsity within $0.2$–$2.7$pp of dense. $2.5$-bit-eq matches dense $3$-bit QAT. Does not retarget GradCodeS or Sparse-BitNet.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.11223`
- Code: none found (`code_status: none`).
