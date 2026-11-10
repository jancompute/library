---
id: method:sga-sparse
type: method
title: 'SGA (SwiGLU-Gate Sparse FFN)'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the deployed checkpoint must stay NF4/INT4/MXFP4 with no high-precision adapter'
  reason: 'GradCodeS remains code-space FT; SGA is native SwiGLU-gate sparsity then QAT'
  use_instead: method:gradcodes
- when: 'native 1.58-bit pretraining from scratch'
  reason: 'Sparse-BitNet remains 1-bit pretrain; SGA is SwiGLU-gate sparsity on a dense FFN'
  use_instead: method:sparse-bitnet
assumptions:
- 'Dense SwiGLU FFN that can be continued-trained. Paper: LLaMA 1B–8B, ~30B tokens, 75–85% FFN sparsity. PTQ of the sparse model degrades; continued-QAT / joint-QAT required. No public code as of 2026-11-10. arXiv 2611.11223 above watermark 2611.09634.'
last_reviewed: '2026-11-10'
papers:
- paper:sga-sparse
recipes:
- recipe:sga-sparse
claims:
- benchmark: 'LLaMA 1B–8B FFN sparsity + QAT'
  metric: 'sparsity / quality vs dense; bit-eq vs dense QAT / ternary'
  value: '75–85% FFN sparsity, 0.2–2.7pp of dense; 2.5-bit-eq matches dense 3-bit QAT; 1.5-bit-eq beats ternary +1.3pp'
  baseline: 'dense / PTQ / ternary'
  date: '2026-11-10'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.11223'
  notes: 'Does not retarget method:gradcodes. PTQ of the sparse model is the failure mode.'
tags:
- sparsity
- swiglu
- quantization
- active
---

# SGA (SwiGLU-Gate Sparse FFN)

## Method Overview
SGA trains the native SwiGLU gate as a top-$k$ router over FFN neurons. After the sparse run, continued-QAT or joint-QAT is required; plain PTQ of the sparse weights degrades.

## When to Use
- Dense SwiGLU models where FFN FLOPs dominate and a mixed sparse+QAT stack is acceptable.

## When NOT to Use
Fully low-bit deployed FT remains `method:gradcodes`. Native 1-bit pretrain remains `method:sparse-bitnet`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:full-lowbit-finetune`. Does **not** replace GradCodeS.

## Gotchas & Failure Modes
- PTQ of the sparse checkpoint is the measured failure. Use continued-QAT / joint-QAT.
- No public trainer.
- Not a MoE architecture template (DeepSeek-V4 / Kimi-K3 stay).
