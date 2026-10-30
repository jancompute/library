---
id: method:a-rsi
type: method
title: 'A-RSI'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'Challenger-Solver-Judge co-evolution from zero external data'
  reason: 'J-Zero remains the data-free first hop; A-RSI refreshes a multimodal task pool from logs'
  use_instead: method:j-zero
assumptions:
- 'Zero external labeled set. Checkable program-generated answers. Project page only as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:a-rsi
recipes:
- recipe:a-rsi
claims:
- benchmark: 'zero-data multimodal RSI vs static task pools / majority-vote targets'
  metric: 'when-to-refresh from train logs'
  value: 'refresh on declining reward variation/accuracy; answers independently checkable'
  baseline: 'static self-play pool; majority-vote pseudo-labels'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.38568'
  notes: 'Does not retarget method:j-zero.'
tags:
- rsi
- multimodal
- active
---

# A-RSI

## Method Overview
A-RSI separates when to get new experience from how to label it. Training-log reward variation and accuracy trigger a task-pool refresh. New multimodal items come from a frozen program library whose answers are checkable, not from self-consistency.

## When to Use
- Zero-external-data multimodal self-play where the current task pool has gone stale.

## When NOT to Use
J-Zero remains Challenger-Solver-Judge first hop. LongZero is long-context RLVR on self-proposed tasks.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:j-zero` or `method:longzero`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- No public GitHub as of 2026-10-30.
- Multimodal program library, not J-Zero's three-role loop.
