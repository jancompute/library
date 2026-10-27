---
id: method:dspark
type: method
title: 'dSpark'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:diffusion-lm-ar-delta-recycle'
  reason: 'A2D recycles an AR weight delta; dSpark distills dLLM unmasking schedules'
  use_instead: method:a2d
- when: 'AR to discrete-dLLM on-policy distillation'
  reason: 'JustOPD distills AR logits; dSpark distills commit schedules'
  use_instead: method:justopd
assumptions:
- 'dLLM schedule distillation. Code VILA-Lab/dSpark.'
last_reviewed: '2026-10-27'
papers:
- paper:dspark
recipes:
- recipe:dspark
claims:
- benchmark: 'Diffusion LM unmasking-schedule distillation vs naive parallel decode'
  metric: 'decoding rounds / quality under KL regularizer'
  value: 'commits tokens whose reveal lowers remaining uncertainty instead of the most confident token'
  baseline: 'confidence-first unmasking; A2D / JustOPD'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.35804'
  notes: 'Does not retarget method:a2d or method:justopd.'
tags:
- diffusion
- dllm
- active
---

# dSpark

## Method Overview
dSpark builds unmasking schedules that reveal tokens which make other masked positions easier, then distills those schedules into the dLLM with a KL term so quality does not collapse.

## When to Use
- Discrete diffusion LMs whose decode cost is dominated by commit order, not AR delta recycle.

## When NOT to Use
Default on `task:diffusion-lm-ar-delta-recycle` remains `method:a2d`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:a2d`.

## Gotchas & Failure Modes
- Not a replacement for `method:a2d`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
