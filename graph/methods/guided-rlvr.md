---
id: method:guided-rlvr
type: method
title: 'Guided-RLVR'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; Guided-RLVR injects steering tokens into the sampler'
  use_instead: method:cispo
- when: 'policy-intrinsic exploration then self-distill (SEPO)'
  reason: 'SEPO elicits a labeled self-teacher; Guided-RLVR steers sampling with thinking tokens'
  use_instead: method:sepo
assumptions:
- 'Math/code RLVR with a lightweight steering-token controller. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:guided-rlvr
recipes:
- recipe:guided-rlvr
claims:
- benchmark: 'Mathematical reasoning and code generation vs RLVR'
  metric: 'accuracy; reasoning-trajectory diversity'
  value: 'consistently outperforms existing RLVR methods while producing more diverse reasoning trajectories'
  baseline: 'RLVR without steering-token injection'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37041'
  notes: 'Does not retarget method:cispo.'
tags:
- rl-alignment
- rlvr
- active
---

# Guided-RLVR

## Method Overview
A lightweight controller injects semantically meaningful steering tokens into the sampling distribution at critical thinking steps so RLVR rollouts do not collapse onto a narrow set of traces.

## When to Use
- Verifiable math/code RL whose rollouts have collapsed onto a few reasoning templates and you can afford a small steering controller.

## When NOT to Use
Default on `task:math-code-rl-dense` remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Not a replacement for `method:cispo`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
