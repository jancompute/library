---
id: method:op-self-training
type: method
title: 'On-Policy Self-Training'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:data-free-self-evolution'
  reason: 'J-Zero remains Challenger-Solver-Judge; this card is data-free on-policy self-distillation from self-proposed QA'
  use_instead: method:j-zero
- when: 'zero-data long-context RL from self-proposed tasks (LongZero)'
  reason: 'LongZero is long-context RLVR on model-proposed tasks; this card is on-policy self-distill'
  use_instead: method:longzero
assumptions:
- 'Self-generated QA plus privileged self-reasoning. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:op-self-training
recipes:
- recipe:op-self-training
claims:
- benchmark: 'Data-free on-policy self-training vs labeled OPSD / external-teacher OPD'
  metric: 'self-improvement without external problems or a stronger teacher'
  value: 'self-generated QA plus privileged self-reasoning instead of ground-truth pairs or a teacher'
  baseline: 'J-Zero; labeled OPSD; teacher OPD'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32770'
  notes: 'Does not retarget method:j-zero.'
tags:
- self-distillation
- data-free
- active
---

# On-Policy Self-Training

## Method Overview
On-policy self-training turns self-generated question-answer pairs and privileged self-reasoning into a data-free self-distillation loop.

## When to Use
- Post-train self-improvement with no external problem set and no stronger teacher.

## When NOT to Use
Default on `task:data-free-self-evolution` remains `method:j-zero`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:j-zero`.

## Gotchas & Failure Modes
- Not a replacement for `method:j-zero`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
