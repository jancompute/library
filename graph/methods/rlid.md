---
id: method:rlid
type: method
title: 'RLiD'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:outcome-only-long-horizon-agent-rl'
  reason: 'CANOPY remains checker coverage; RLiD is decision-plane RL'
  use_instead: method:canopy
- when: 'variable environment latency / async stragglers'
  reason: 'SAO remains async RL; RLiD is a decision-plane action selector'
  use_instead: method:sao
assumptions:
- 'Decision-plane RL then optional trajectory distill. Mention on task:agentic-async-rl. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:rlid
recipes:
- recipe:rlid
claims:
- benchmark: 'ALFWorld; also ARC / Countdown / Sokoban'
  metric: 'success / H100-hours vs token-level RL'
  value: 'ALFWorld 99.3% in 12.7 H100-h vs 86.6% in 17.3h; 100% on 134 unseen with memory'
  baseline: 'token-level RL on the same tasks'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.02455'
  notes: 'Does not retarget method:canopy or method:sao. Mention on task:agentic-async-rl.'
tags:
- agents
- decision-rl
- active
---

# RLiD

## Method Overview
RLiD RL-trains a single-pass action selector over a labeled menu, then optionally distills those action traces into a generative LLM.

## When to Use
- Interactive agents whose environment only executes a parsed action and token-level credit is noisy.

## When NOT to Use
CANOPY remains checker coverage. SAO remains async stragglers.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy` or `method:sao`.

## Gotchas & Failure Modes
- Requires an action menu the environment can execute.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
