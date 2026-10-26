---
id: method:multi-view-opsd
type: method
title: 'Multi-View OPSD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:privileged-teacher-opsd'
  reason: 'VISTA remains single-reference gold OPSD; multi-view OPSD conditions the teacher on several realizations of the solution'
  use_instead: method:vista
assumptions:
- 'Privileged same-size teacher with a reference solution. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:multi-view-opsd
recipes:
- recipe:multi-view-opsd
claims:
- benchmark: 'Privileged OPSD vs single complete-reference teacher'
  metric: 'sensitivity of OPSD to the particular gold reference'
  value: 'multiple teacher views of the reference reduce single-realization sensitivity vs one complete-reference teacher'
  baseline: 'single complete-reference VISTA-style OPSD'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.30880'
  notes: 'Does not retarget method:vista.'
tags:
- distillation
- opsd
- active
---

# Multi-View OPSD

## Method Overview
Multi-view OPSD treats a gold reference as one realization and trains against several teacher views so the student is less tied to one write-up.

## When to Use
- Privileged OPSD where one gold trace overfits the student to that write-up.

## When NOT to Use
Default on `task:privileged-teacher-opsd` remains `method:vista`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:vista`.

## Gotchas & Failure Modes
- Not a replacement for `method:vista`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
