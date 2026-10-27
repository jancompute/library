---
id: method:doublefree
type: method
title: 'DoubleFree'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:student-distillation'
  reason: 'OPD remains matching; DoubleFree consolidates domain RL traces without live student rollouts'
  use_instead: method:opd
- when: 'multi-teacher distillation'
  reason: 'Open-MOPD remains multi-teacher; DoubleFree is rollout-free consolidation of historical RL traces'
  use_instead: method:open-mopd
assumptions:
- 'Offline consolidation after domain RL. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:doublefree
recipes:
- recipe:doublefree
claims:
- benchmark: 'Multi-task specialist consolidation vs live MOPD'
  metric: 'rollout and teacher-online cost at consolidation'
  value: 'reuses domain-RL trajectories and precomputed teacher logp so consolidation is rollout-free and teacher-offline'
  baseline: 'live multi-teacher OPD after independent domain RL'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.34272'
  notes: 'Does not retarget method:opd or method:open-mopd.'
tags:
- distillation
- mopd
- active
---

# DoubleFree

## Method Overview
DoubleFree treats domain RL traces as exploration history, precomputes teacher targets on those traces, and consolidates specialists without sampling the student or keeping teachers online.

## When to Use
- Multi-task post-train that already ran per-domain RL and cannot afford a second live MOPD pass.

## When NOT to Use
Default on `task:student-distillation` remains `method:opd`. Multi-teacher remains `method:open-mopd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Not a replacement for `method:opd`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
