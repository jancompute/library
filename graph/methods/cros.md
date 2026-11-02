---
id: method:cros
type: method
title: 'CRoS'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; CRoS adds a scramble-order causality reward on a GRPO host'
  use_instead: method:cispo
assumptions:
- 'Dense math/logic RLVR with a CoT that can be step-scrambled. Project page only; no public GitHub as of 2026-11-02.'
last_reviewed: '2026-11-02'
papers:
- paper:cros
recipes:
- recipe:cros
claims:
- benchmark: 'Reasoning Gym Gemma-3-4B, five unseen logic/games sets'
  metric: 'OOD accuracy / CoT-Pass@K avg / hint acknowledgment'
  value: '46.8 vs 43.8 / 43.4 vs 41.4 / 34.0 vs 20.2'
  baseline: 'outcome reward and deletion/error-injection causality rewards'
  date: '2026-11-02'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.42054'
  notes: 'Does not retarget method:cispo.'
tags:
- rlvr
- causality
- active
---

# CRoS

## Method Overview
CRoS rewards CoT causality by scrambling reasoning-step order without changing step content, so the metric is not confounded by information deletion or error injection.

## When to Use
- Outcome RLVR where you also need the CoT to cause the answer, not just match it.

## When NOT to Use
CISPO remains Pass@1 dense RLVR.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Deletion/error-injection causality rewards can shrink informative CoTs and cut exploration.
- Paper claims are dated 2026-11-02; no locked-SOTA bake-off.
- No public GitHub as of 2026-11-02.
