---
id: method:mta-opsd
type: method
title: 'MTA-OPSD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:privileged-teacher-opsd'
  reason: 'VISTA remains gold-solution OPSD; MTA-OPSD routes a teacher per token'
  use_instead: method:vista
assumptions:
- 'Privileged references. Official code xingzhejun/MTA-OPSD.'
last_reviewed: '2026-10-30'
papers:
- paper:mta-opsd
recipes:
- recipe:mta-opsd
claims:
- benchmark: 'token-level teacher-intervention pilot + OPSD'
  metric: 'teacher selection by vote/KL vs fixed full-reference teacher'
  value: 'preferred teacher varies token-by-token inside one response'
  baseline: 'fixed full-reference OPSD; response-level adaptive exposure'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.40574'
  notes: 'Does not retarget method:vista.'
tags:
- opsd
- multi-teacher
- active
---

# MTA-OPSD

## Method Overview
MTA-OPSD builds several privileged teachers (different reference exposure) and, for each student token, picks the teacher preferred by majority vote plus KL. One response is not one teacher.

## When to Use
- Privileged OPSD where a single gold view is the wrong teacher on some tokens.

## When NOT to Use
VISTA remains the privileged-teacher first hop.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:vista` or `method:multi-view-opsd`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Multi-teacher decode cost per token.
