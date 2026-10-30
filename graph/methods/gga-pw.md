---
id: method:gga-pw
type: method
title: 'GGA-PW'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:linear-time-sequence-modeling'
  reason: 'Mamba-2 remains the architecture hop; GGA-PW is GDN state quant'
  use_instead: method:mamba-2
- when: 'periodic 4-bit recurrent-state quantization (PACE)'
  reason: 'PACE is periodic rounding plus a token buffer; GGA-PW is GDN mixed-precision plus pure-write'
  use_instead: method:pace
assumptions:
- 'Gated DeltaNet recurrent state. Mixed-precision heads plus FP8 recency window. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:gga-pw
recipes:
- recipe:gga-pw
claims:
- benchmark: 'low-bit GDN long-reasoning vs uniform state quant'
  metric: 'quality / repetition / output length'
  value: 'gradient-aware mixed bits plus FP8 pure-write window'
  baseline: 'uniform low-bit GDN writeback'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.39931'
  notes: 'Does not retarget method:mamba-2 or method:pace.'
tags:
- gdn
- quantization
- active
---

# GGA-PW

## Method Overview
GGA-PW is GDN-specific recurrent-state quantization. GGA spends bits where write residuals hurt future loss. PW holds a short FP8 pure-write window so the newest tokens are not immediately rounded into the low-bit state.

## When to Use
- Gated DeltaNet / linear-attention decode where 4-bit state writeback causes repetition and overlong outputs.

## When NOT to Use
Architecture first hop remains Mamba-2. Periodic 4-bit SSM state remains PACE.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:mamba-2` or `method:pace`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- No public code as of 2026-10-30.
- GDN-specific; not a generic SSM quant.
