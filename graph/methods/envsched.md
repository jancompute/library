---
id: method:envsched
type: method
title: 'EnvSched'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agentic-async-rl'
  reason: 'SAO remains async straggler RL; EnvSched schedules environment-task pairs under a finite rollout budget'
  use_instead: method:sao
- when: 'outcome-only long-horizon agent RL (coverage / anti-drift)'
  reason: 'CANOPY remains checker-backed coverage; EnvSched is env-task rollout scheduling'
  use_instead: method:canopy
assumptions:
- 'Online scheduler over environment-task pairs with exploitation vs coverage. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:envsched
recipes:
- recipe:envsched
claims:
- benchmark: 'Agent RL with executable environments under a finite rollout budget'
  metric: 'rollout efficiency via exploitation of informative reward gaps and coverage of underobserved envs'
  value: 'schedules environment-task pairs from rollout history so the batch is not spent on uninformative or overobserved instances'
  baseline: 'uniform or difficulty-agnostic env-task sampling'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37609'
  notes: 'Does not retarget method:sao.'
tags:
- rl-alignment
- agentic
- scheduling
- active
---

# EnvSched

## Method Overview
EnvSched scores environment-task pairs for informative reward differences (exploitation) and underobserved interaction patterns (coverage), then schedules the finite rollout budget over that dual graph.

## When to Use
- Agentic RL whose bottleneck is which env/task to roll out next, not straggler latency inside a chosen env.

## When NOT to Use
Default on `task:agentic-async-rl` remains `method:sao`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:sao`.

## Gotchas & Failure Modes
- Not a replacement for `method:sao`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
