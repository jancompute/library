---
id: method:scarl
type: method
title: 'SCARL'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; SCARL reshapes advantages by sequence-confidence gap'
  use_instead: method:cispo
assumptions:
- 'GRPO-family group advantages. Official code kezhh163/scarl.'
last_reviewed: '2026-10-30'
papers:
- paper:scarl
recipes:
- recipe:scarl
claims:
- benchmark: 'RLVR sequence-confidence alignment vs base GRPO-family estimator'
  metric: 'advantage reshape / entropy'
  value: 'never re-signs; reduces to the base estimator when already aligned'
  baseline: 'GRPO/CISPO-family group advantage'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.40407'
  notes: 'Does not retarget method:cispo.'
tags:
- rlvr
- confidence
- active
---

# SCARL

## Method Overview
SCARL keeps the sign of the group advantage and reallocates its magnitude toward sequences whose confidence disagrees with the verifier outcome: boost barely-found successes, hit confident errors harder, and equalize confidence among same-advantage responses.

## When to Use
- Dense RLVR where entropy collapse and lucky-success updates are both visible.

## When NOT to Use
CISPO remains Pass@1.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Reshape only; if the base advantage is wrong, SCARL cannot save it.
