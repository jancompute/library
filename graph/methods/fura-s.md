---
id: method:fura-s
type: method
title: 'FuRA-S'
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:4bit-peft-quantization'
  reason: 'AQLoRA-Q remains 4-bit PEFT; FuRA-S is forward-only spectral specialists'
  use_instead: method:aqlora-q
assumptions:
- 'On-device specialists, not a LoRA adapter bake-off. Mention on task:full-lowbit-finetune. No public code as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:fura-s
recipes:
- recipe:fura-s
claims:
- benchmark: 'phone-use specialists'
  metric: 'success rate at 1–5 MB INT4'
  value: '6–23% to 89–100%'
  baseline: 'unadapted on-device policy'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.04797'
  notes: 'Does not retarget method:aqlora-q or method:gradcodes.'
tags:
- peft
- quantization
- active
---

# FuRA-S

## Method Overview
FuRA-S trains tiny forward-only block-spectral specialists so an INT4 base can pick up a phone-use skill without editing weights.

## When to Use
- On-device INT4 specialists when a mixed-precision LoRA adapter is not allowed and the skill is narrow.

## When NOT to Use
AQLoRA-Q remains 4-bit PEFT. GradCodeS remains fully low-bit code-space FT.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:aqlora-q` or `method:gradcodes`.

## Gotchas & Failure Modes
- Forward-only ES, not backprop LoRA.
- No public code as of 2026-11-04.
