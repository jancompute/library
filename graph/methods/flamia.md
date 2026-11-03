---
id: method:flamia
type: method
title: 'FLAMIA'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:fp4-hardware-training'
  reason: 'Quartet-II remains NVFP4 training; FLAMIA is Blackwell attention kernels'
  use_instead: method:quartet-ii
assumptions:
- 'Blackwell B200/B300 packed-document causal attention. Official code yandex-research/flamia-blackwell-attention.'
last_reviewed: '2026-11-03'
papers:
- paper:flamia
recipes:
- recipe:flamia
claims:
- benchmark: 'causal packed-document attention on B200 / B300'
  metric: 'fwd+bwd attention including quantization vs fastest baseline'
  value: '1.10-1.40x B200; 1.06-1.42x B300'
  baseline: 'fastest evaluated attention baseline per workload'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03344'
  notes: 'Code yandex-research/flamia-blackwell-attention. Does not retarget method:quartet-ii.'
tags:
- fp4
- attention
- blackwell
- active
---

# FLAMIA

## Method Overview
FLAMIA trains attention in MXFP8 or mixed NVFP4/FP8 on Blackwell with token-block scales that do not leak future tokens and with matched forward/backward numerics.

## When to Use
- Native FP4/FP8 attention training on Blackwell B200/B300 at long context.

## When NOT to Use
Quartet-II remains NVFP4 hardware training default. MXFP4-MI355X remains the MXFP4 co-default.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:quartet-ii` or `method:mxfp4-mi355x`.

## Gotchas & Failure Modes
- Kernel family, not a full NVFP4 pretrain recipe.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
