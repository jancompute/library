---
id: method:sgr-opsd
type: method
title: 'SGR-OPSD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:outcome-only-long-horizon-agent-rl'
  reason: 'CANOPY remains checker coverage; SGR-OPSD is subgoal-graph privileged OPSD'
  use_instead: method:canopy
assumptions:
- 'ALFWorld / WebShop / Search-QA, Qwen2.5-3B/7B. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:sgr-opsd
recipes:
- recipe:sgr-opsd
claims:
- benchmark: 'ALFWorld / WebShop / Search-QA, Qwen2.5-3B and 7B'
  metric: 'success rate vs GRPO'
  value: 'ALFWorld 7B 85.8%; up to +7.4 vs GRPO'
  baseline: 'GRPO and self-distillation baselines'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.02414'
  notes: 'Does not retarget method:canopy.'
tags:
- opsd
- agents
- active
---

# SGR-OPSD

## Method Overview
SGR-OPSD uses subgoal plans as dense privileged weights, then rescales those weights from a progress graph built on sampled transitions.

## When to Use
- Long-horizon agents with privileged OPSD where logp gaps do not track subgoal progress.

## When NOT to Use
CANOPY remains checker-based outcome-only coverage.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy`.

## Gotchas & Failure Modes
- Paper GRPO numbers are not a CANOPY bake-off.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
