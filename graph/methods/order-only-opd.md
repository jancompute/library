---
id: method:order-only-opd
type: method
title: 'Order-Only OPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'same-tokenizer single-teacher matching distillation'
  reason: 'OPD remains probability matching; O3PD is ordinal top-K only'
  use_instead: method:opd
assumptions:
- 'Six teacher-student pairs on HMMT25/AIME24/AIME25. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:order-only-opd
recipes:
- recipe:order-only-opd
claims:
- benchmark: 'HMMT25 / AIME24 / AIME25, six teacher-student pairs'
  metric: 'average / AIME25 vs OPD'
  value: 'beats OPD in every pair, up to +2.9 avg / +5.6 AIME25'
  baseline: 'probability-matching OPD'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.02112'
  notes: 'Does not retarget method:opd.'
tags:
- opd
- ordinal
- active
---

# Order-Only OPD

## Method Overview
O3PD matches the teacher's top-K token order on student prefixes and ignores probability magnitudes, removing teacher-temperature sensitivity.

## When to Use
- OPD where teacher temperature or calibration is a confound and ranking is enough.

## When NOT to Use
OPD remains the matching default when you want probability values.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Departs further from teacher probabilities than OPD while matching ranking more faithfully.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
