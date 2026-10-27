---
id: method:gpdpo
type: method
title: 'GPDPO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:multi-reward-rlvr'
  reason: 'CorrGRPO/DARA remain aggregation defaults; GPDPO recovers Pareto pairs from conflict-filtered rollouts'
  use_instead: method:corrgrpo
assumptions:
- 'Multi-reward conflict reuse. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:gpdpo
recipes:
- recipe:gpdpo
claims:
- benchmark: 'API-Bank multi-reward RL vs conflict-filter baselines'
  metric: 'task score; group-relative and pairwise reward conflicts'
  value: 'beats paper multi-reward baselines across scales; reduces group-relative and pairwise conflicts'
  baseline: 'reward reweight / gradient coordination / rollout filter; CorrGRPO / DARA'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.35480'
  notes: 'Does not retarget method:corrgrpo or method:dara.'
tags:
- rl-alignment
- multi-reward
- active
---

# GPDPO

## Method Overview
GPDPO keeps conflict-filtered rollouts as pairwise Pareto preferences so discarded multi-reward samples still supervise the policy without extra sampling.

## When to Use
- Multi-reward RL that filters conflicting groups and throws away usable pairwise order.

## When NOT to Use
Default on `task:multi-reward-rlvr` remains `method:corrgrpo` + `method:dara`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:corrgrpo`.

## Gotchas & Failure Modes
- Not a replacement for `method:corrgrpo`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
