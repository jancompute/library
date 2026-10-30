---
id: method:tesd
type: method
title: 'TESD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:privileged-teacher-opsd'
  reason: 'VISTA remains gold-solution privileged OPSD; TESD evolves the self-teacher from rollout rewards'
  use_instead: method:vista
assumptions:
- 'Privileged gold context available. Same-size self-teacher. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:tesd
recipes:
- recipe:tesd
claims:
- benchmark: 'multi-dataset multi-scale OPSD vs token-level and sequence-level OPSD'
  metric: 'downstream accuracy'
  value: 'TESD consistently outperforms representative OPSD baselines'
  baseline: 'vanilla OPSD / token-level and sequence-level self-distill'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.38637'
  notes: 'Does not retarget method:vista.'
tags:
- opsd
- distillation
- active
---

# TESD

## Method Overview
TESD splits privileged OPSD into teacher-oriented and student-oriented updates. The self-teacher generates rollouts and is scored on correctness and whether it still needs the privileged context. Those rewards train the teacher and gate how hard the student follows it.

## When to Use
- Privileged OPSD that stalls because the gold-conditioned self-teacher is a poor teacher on some prompts.

## When NOT to Use
First hop on `task:privileged-teacher-opsd` remains `method:vista`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:vista`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- No public code as of 2026-10-30.
