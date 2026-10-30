---
id: method:mass-opsd
type: method
title: 'MASS'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:privileged-teacher-opsd'
  reason: 'VISTA remains gold-solution OPSD; MASS masks multiple views of one solution'
  use_instead: method:vista
assumptions:
- 'One verified gold solution that can be masked. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:mass-opsd
recipes:
- recipe:mass-opsd
claims:
- benchmark: 'math reasoning OPSD vs single-reference self-distill'
  metric: 'accuracy'
  value: 'consistently outperforms strong self-distillation baselines'
  baseline: 'single-reference privileged OPSD'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.38154'
  notes: 'Does not retarget method:vista.'
tags:
- opsd
- active
---

# MASS

## Method Overview
MASS builds several masked views of one verified solution so the privileged teacher is not a single leaked trace. It aggregates those views and keeps only the token-level corrections that agree.

## When to Use
- Privileged OPSD that overfits the surface form of one gold solution.

## When NOT to Use
VISTA remains the privileged-teacher first hop.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:vista` or `method:multi-view-opsd`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- No public code as of 2026-10-30.
