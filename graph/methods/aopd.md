---
id: method:aopd
type: method
title: 'AOPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:student-distillation'
  reason: 'OPD remains matching at every student state; AOPD follows the teacher only when the advantage says it helps the student'
  use_instead: method:opd
assumptions:
- 'On-policy student rollouts with a teacher logp. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:aopd
recipes:
- recipe:aopd
claims:
- benchmark: 'On-policy distillation vs always-follow-teacher OPD'
  metric: 'whether teacher guidance at a student state improves the student'
  value: 'gates teacher matching by advantage so the student does not imitate teacher actions that do not help'
  baseline: 'standard OPD / always-follow-teacher on-policy distillation'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.31563'
  notes: 'Does not retarget method:opd.'
tags:
- distillation
- opd
- active
---

# AOPD

## Method Overview
AOPD distinguishes teacher preference from student improvement and matches the teacher only on states where the advantage says following helps.

## When to Use
- OPD where the teacher is locally preferred but following it does not raise student return.

## When NOT to Use
Default on `task:student-distillation` remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Not a replacement for `method:opd`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
