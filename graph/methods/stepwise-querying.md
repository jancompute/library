---
id: method:stepwise-querying
type: method
title: 'Stepwise Querying'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:student-distillation'
  reason: 'OPD remains matching when teacher logp is available; Stepwise Querying is black-box SFT'
  use_instead: method:opd
- when: 'family-native reasoning traces when the teacher hides CoT (TraceForge)'
  reason: 'TraceForge regenerates student-family traces from a teacher answer; Stepwise Querying queries the teacher for step details'
  use_instead: method:traceforge
assumptions:
- 'Black-box teacher that answers step queries. No public code as of 2026-11-02.'
last_reviewed: '2026-11-02'
papers:
- paper:stepwise-querying
recipes:
- recipe:stepwise-querying
claims:
- benchmark: 'Two teachers, two students, four math/code benches vs three black-box baselines'
  metric: 'win count'
  value: 'highest score in 14 of 16 comparisons'
  baseline: 'global teacher solution SFT; TraceForge-style hidden-CoT reconstruction not the paper bake-off'
  date: '2026-11-02'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.41769'
  notes: 'Does not retarget method:opd. Sibling of method:traceforge.'
tags:
- distillation
- black-box
- active
---

# Stepwise Querying

## Method Overview
Stepwise Querying elicits intermediate derivations, validity checks, and corrections from a black-box teacher that withholds CoT, then trains the student with ordinary SFT on the assembled solutions.

## When to Use
- Distillation when the teacher returns answers but not internal CoT, and you can query that same teacher per step.

## When NOT to Use
Teacher logp available → `method:opd`. Teacher answer without a queryable step API → `method:traceforge`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`. Sibling of `method:traceforge`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-11-02; no locked-SOTA bake-off.
- Incorrect-answer trajectories can still help if intermediate steps are valid; further decomposition yields limited extra gain.
- No public code as of 2026-11-02.
