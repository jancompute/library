---
id: method:mpopd
type: method
title: 'MPOPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:student-distillation'
  reason: 'OPD remains single-teacher matching; MPOPD changes the student rollout proposal to a teacher-guided geometric mixture'
  use_instead: method:opd
- when: 'multi-teacher distillation'
  reason: 'Open-MOPD remains multi-teacher; MPOPD is a single-teacher rollout-proposal change'
  use_instead: method:open-mopd
assumptions:
- 'Student-anchored teacher-guided geometric-mixture proposal. Code: csr16/MPOPD.'
last_reviewed: '2026-10-28'
papers:
- paper:mpopd
recipes:
- recipe:mpopd
claims:
- benchmark: '16 math, knowledge, and medical reasoning benches; Qwen3-4B-Base math'
  metric: 'average accuracy; mean generation length'
  value: '+6.91 average math accuracy over OPD on Qwen3-4B-Base with 41% shorter generations; consistent gains vs OPD and recent variants'
  baseline: 'OPD with student-only rollouts'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36477'
  notes: 'Does not retarget method:opd.'
tags:
- distillation
- opd
- active
---

# MPOPD

## Method Overview
MPOPD treats the OPD rollout policy as the thing to optimize. It approximates a geometric mixture of student and teacher from a local trust-region on relative teacher support, then samples that proposal in one forward pass so the teacher is not asked to supervise unreachable student traces.

## When to Use
- Single-teacher OPD where student rollouts leave the teacher's support and the student starts repeating or drifting.

## When NOT to Use
Default on `task:student-distillation` remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Not a replacement for `method:opd`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
