---
id: method:datc
type: method
title: 'DATC'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains sequence-IS Pass@1; DATC reweights tokens by the RM-gradient component along the sampled action'
  use_instead: method:cispo
assumptions:
- 'Reward model differentiable wrt token logp. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:datc
recipes:
- recipe:datc
claims:
- benchmark: 'GRPO-style shared advantage vs direction-aware token credit from RM grads'
  metric: 'token credit aligned with increasing reward vs broadcasting one response advantage'
  value: 'work-style token credit from the RM gradient component along the sampled token'
  baseline: 'GRPO shared advantage; CISPO token-IS'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32772'
  notes: 'Does not retarget method:cispo.'
tags:
- rlvr
- credit
- active
---

# DATC

## Method Overview
DATC treats token credit as work: the component of the reward-model gradient along the sampled token, instead of broadcasting one response-level advantage.

## When to Use
- RLVR or RM-shaped RL where a shared group advantage updates tokens against the local reward gradient.

## When NOT to Use
Default on `task:math-code-rl-dense` remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Not a replacement for `method:cispo`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
