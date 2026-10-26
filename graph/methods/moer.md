---
id: method:moer
type: method
title: 'MOER'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains on-policy Pass@1; MOER mixes expert prefixes then rolls back unhelpful guidance'
  use_instead: method:cispo
assumptions:
- 'Mix-policy RL with expert prefixes. Code CityU-MLO/MOER.'
last_reviewed: '2026-10-26'
papers:
- paper:moer
recipes:
- recipe:moer
claims:
- benchmark: 'Mix-policy reasoning RL vs static full-trace expert guidance / unguarded prefix guidance'
  metric: 'stability of mix-policy RL and final reasoning accuracy'
  value: 'selective rollback of unhelpful expert prefixes vs static full-trace guidance that suppresses exploration'
  baseline: 'on-policy RL; static full-trace expert guidance; unguarded expert prefixes'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.30873'
  notes: 'Does not retarget method:cispo.'
tags:
- rlvr
- mix-policy
- active
---

# MOER

## Method Overview
MOER mixes off-policy expert prefixes into on-policy RL and rolls back guidance that is not correctness-preserving so exploration is not suppressed.

## When to Use
- RLVR that has expert traces but static full-trace guidance collapses exploration.

## When NOT to Use
Default on `task:math-code-rl-dense` remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Not a replacement for `method:cispo`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
