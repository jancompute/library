---
id: method:bred
type: method
title: BReD
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'full-param memory-efficient pretrain via subspace projections'
  reason: 'SCALE remains that first hop; BReD dithers EMA optimizer states'
  use_instead: method:scale
- when: '4-bit AdamW optimizer-state quantization in preconditioner space (ZIP-SR)'
  reason: 'ZIP-SR is AdamW second-moment codebook plus preconditioner-space SR; BReD is EMA subtractive dither'
  use_instead: method:zip-sr
- when: 'choosing the ~7B dense pretrain optimizer'
  reason: 'Muon2 remains the 7B default; BReD is a low-bit EMA-state wrapper'
  use_instead: method:muon2
assumptions:
- 'Host optimizer keeps its update and HPs. EMA states only. Paper: five optimizers at 120M; AdamW/Muon 1.1B–3.4B pretrain and 7B FT. Code ZhanHeshen/BReD.'
last_reviewed: '2026-11-27'
papers:
- paper:bred
recipes:
- recipe:bred
claims:
- benchmark: '4-bit EMA optimizer states vs full precision (120M five-opt; 1.1B/3.4B AdamW+Muon; 7B FT)'
  metric: 'PPL shift / downstream'
  value: 'PPL ≤0.5 pretrain / ≤0.2 FT; downstream within 0.7'
  baseline: 'full-precision optimizer states; nearest/SR under the same grid'
  date: '2026-11-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.33951'
  notes: '3-bit still converges in the paper. Does not retarget SCALE, ZIP-SR, or Muon2. Code ZhanHeshen/BReD.'
tags:
- optimizer
- quantization
- ema
- 4bit
- active
---

# BReD

## Method Overview
BReD stores EMA optimizer states in low bits by subtractive dithering: a block-shared dither is added before quantize and subtracted after dequantize. The dither is regenerated from a deterministic seed, so no extra random tensor lives on GPU. The host optimizer (AdamW, Muon, SOAP, …) is otherwise unchanged.

## When to Use
- Full-param training where EMA optimizer-state memory is the constraint and the original update / HPs must stay put.

## When NOT to Use
Subspace first hop remains SCALE. AdamW second-moment codebook remains ZIP-SR. The 7B optimizer remains Muon2.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:scale`, `method:zip-sr`, or `method:muon2`.

## Gotchas & Failure Modes
- EMA-specific: non-EMA states do not inherit the \(e_{t+1}=\beta e_t+\epsilon_{t+1}\) argument.
- Same grid with nearest or stochastic rounding can still diverge; the dither is the method.
- No SCALE bake-off.
