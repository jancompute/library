---
id: method:error-diffusion
type: method
title: 'Error-Diffusion Binary Weights'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:1bit-extreme-quantization'
  reason: 'Sparse-BitNet remains native 1.58-bit pretrain; error diffusion replaces latent+Adam state for on-device binary adapts'
  use_instead: method:sparse-bitnet
assumptions:
- 'Binary-weight on-device training without full-precision latents. Code pierreolivierbonin/error-diffusion-binary-weight-lms.'
last_reviewed: '2026-10-27'
papers:
- paper:error-diffusion
recipes:
- recipe:error-diffusion
claims:
- benchmark: 'Binary-weight training-state bits vs latent+Adam'
  metric: 'bits per weight; binary MLP match of 4-bit vs 8-bit buffers'
  value: '97 bits to 3-9 per weight (up to 19x); threshold-aligned 4-bit matches 8-bit on a binary MLP'
  baseline: 'full-precision latent + Adam (~96 extra bits/weight)'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.34566'
  notes: 'Does not retarget method:sparse-bitnet.'
tags:
- quantization
- 1bit
- active
---

# Error-Diffusion Binary Weights

## Method Overview
Error diffusion stores a low-bit residual of each update and flips the binary weight only when that residual crosses the quantization threshold, so the device does not keep a latent FP copy plus Adam.

## When to Use
- Binary deployed weights that must be adapted on the same device without a 96-bit optimizer state.

## When NOT to Use
Default on `task:1bit-extreme-quantization` remains `method:sparse-bitnet`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:sparse-bitnet`.

## Gotchas & Failure Modes
- Not a replacement for `method:sparse-bitnet`.
- Threshold-alignment is required; misaligned grids fail.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
