---
id: method:sepo
type: method
title: 'SEPO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; SEPO is label-elicited self-teacher exploration then distill'
  use_instead: method:cispo
- when: 'intentional single-teacher matching distillation'
  reason: 'OPD remains matching; SEPO is policy-intrinsic exploration plus self-distill'
  use_instead: method:opd
assumptions:
- 'Labeled RLVR exploration bottleneck. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:sepo
recipes:
- recipe:sepo
claims:
- benchmark: 'Scientific / tool-use / logical reasoning vs RLVR and OPSD at matched time'
  metric: 'accuracy under identical training time or steps'
  value: 'best among paper comparators at matched time or steps by eliciting then distilling in-distribution solutions'
  baseline: 'RLVR; on-policy self-distillation'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.34137'
  notes: 'Does not retarget method:cispo.'
tags:
- rl-alignment
- active
---

# SEPO

## Method Overview
SEPO uses labels to elicit a correct in-distribution trace when the policy cannot sample one, then treats that conditioned policy as a self-teacher and distills the new solution back.

## When to Use
- Verifiable reasoning RL that stalls because no correct rollout appears, and external demos would be off-policy.

## When NOT to Use
Default on `task:math-code-rl-dense` remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Not a replacement for `method:cispo`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
