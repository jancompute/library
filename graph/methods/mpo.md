---
id: method:mpo
type: method
title: 'MPO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:outcome-only-long-horizon-agent-rl when a checker exists'
  reason: 'CANOPY remains coverage; MPO is turn-scale advantage plus turn-level IS'
  use_instead: method:canopy
- when: 'variable environment latency / async stragglers'
  reason: 'SAO remains async; MPO is multiscale credit, not straggler replay'
  use_instead: method:sao
assumptions:
- 'Turn-scale agent RL. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:mpo
recipes:
- recipe:mpo
claims:
- benchmark: '4B / 30B-A3B search, tool-use, and automation vs strong RL baselines'
  metric: 'task success vs SAO-style / group RL hosts'
  value: 'consistent gains by anchoring credit at turns then splitting tokens'
  baseline: 'token-IS agent RL; SAO; CANOPY-style outcome groups'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.35013'
  notes: 'Does not retarget method:canopy or method:sao.'
tags:
- rl-alignment
- agentic
- active
---

# MPO

## Method Overview
MPO estimates advantages at the assistant-turn scale, applies turn-level importance sampling, and only then distributes token credit, matching where critic values actually move.

## When to Use
- Long-horizon tool agents whose value changes between turns more than between tokens.

## When NOT to Use
Default on `task:outcome-only-long-horizon-agent-rl` remains `method:canopy`. Async remains `method:sao`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy` or `method:sao`.

## Gotchas & Failure Modes
- Not a replacement for `method:canopy`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
