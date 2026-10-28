---
id: method:nld-uni
type: method
title: 'NLD-Uni'
category: diffusion
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:diffusion-lm-ar-delta-recycle'
  reason: 'A2D remains AR-delta recycle onto a converted dLLM; NLD-Uni is cross-paradigm OPD into a unified discrete diffusion LLM'
  use_instead: method:a2d
- when: 'AR to discrete-dLLM on-policy distillation (JustOPD)'
  reason: 'JustOPD is AR to text dLLM OPD; NLD-Uni transfers AR VLM understanding and flow generation into one discrete diffusion model'
  use_instead: method:justopd
- when: 'intentional single-teacher text matching distillation'
  reason: 'OPD remains text matching; NLD-Uni is unified visual understanding/generation diffusion OPD'
  use_instead: method:opd
assumptions:
- 'Unified discrete diffusion LLM for visual understanding and generation. Progressive self-refining corruption vs absorbing masks. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:nld-uni
recipes:
- recipe:nld-uni
claims:
- benchmark: 'Unified visual understanding and generation vs prior unified diffusion models'
  metric: 'transfer of AR VLM understanding and continuous-flow generation into a discrete diffusion LLM'
  value: 'cross-paradigm OPD plus progressive self-refining diffusion that can commit tokens mid-trajectory instead of absorbing-mask corruption'
  baseline: 'prior unified diffusion models with absorbing-mask training'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36466'
  notes: 'Does not retarget method:a2d.'
tags:
- diffusion
- dllm
- opd
- active
---

# NLD-Uni

## Method Overview
NLD-Uni distills an AR VLM and a continuous flow model into one discrete diffusion LLM with cross-paradigm OPD, and trains a progressive self-refining corruption process so inference can commit tokens before the last step.

## When to Use
- You want one discrete diffusion checkpoint to inherit AR visual understanding and flow generation, not an AR weight-delta recycle.

## When NOT to Use
Default on `task:diffusion-lm-ar-delta-recycle` remains `method:a2d`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:a2d`.

## Gotchas & Failure Modes
- Not a replacement for `method:a2d`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
