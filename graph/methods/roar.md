---
id: method:roar
type: method
title: 'RoAR'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; RoAR adds agreement rewards among verified-correct GRPO traces'
  use_instead: method:cispo
assumptions:
- 'GRPO-family agreement on correct rollouts. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:roar
recipes:
- recipe:roar
claims:
- benchmark: 'GRPO with rollout-agreement reward vs vanilla GRPO'
  metric: 'spurious-reasoning rate among correct traces; downstream accuracy'
  value: 'low-agreement correct traces 35% spurious vs 22% high-agreement across 126 pairs; RoAR rewards agreement on verified-correct rollouts'
  baseline: 'GRPO outcome-only group rewards'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.34951'
  notes: 'Does not retarget method:cispo.'
tags:
- rl-alignment
- active
---

# RoAR

## Method Overview
RoAR keeps GRPO's verifier reward and adds a reasoning-level agreement term among verified-correct rollouts so the policy is not updated equally on internally inconsistent lucky traces.

## When to Use
- Group RLVR where several correct answers exist but some traces are internally wrong.

## When NOT to Use
Default on `task:math-code-rl-dense` remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Not a replacement for `method:cispo`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
