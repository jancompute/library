---
id: method:steer-teacher
type: method
title: 'Steered-Teacher OPSD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:privileged-teacher-opsd'
  reason: 'VISTA remains gold-solution privileged OPSD; ST-OPSD steers teacher activations against reference hallucination'
  use_instead: method:vista
assumptions:
- 'Privileged OPSD on thinking models. Teacher is steered; student is not. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:steer-teacher
recipes:
- recipe:steer-teacher
claims:
- benchmark: 'AIME / HMMT privileged OPSD vs vanilla OPSD'
  metric: 'accuracy; reconsideration; reference-hallucination rate'
  value: 'beats vanilla OPSD; restores reconsideration and reference-hallucination rates to the base model'
  baseline: 'vanilla privileged OPSD'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.34005'
  notes: 'Does not retarget method:vista.'
tags:
- distillation
- opsd
- active
---

# Steered-Teacher OPSD

## Method Overview
ST-OPSD extracts reference-citing and reconsideration directions from traces and adds them to the teacher's hidden states when writing distillation targets, so the student never sees a teacher that quotes the gold solution or forbids revision.

## When to Use
- Privileged OPSD on thinking models that start citing an unseen reference or skip verification.

## When NOT to Use
Default on `task:privileged-teacher-opsd` remains `method:vista`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:vista`.

## Gotchas & Failure Modes
- Not a replacement for `method:vista`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
