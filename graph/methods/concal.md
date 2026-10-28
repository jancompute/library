---
id: method:concal
type: method
title: 'ConCal'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:outcome-only-long-horizon-agent-rl'
  reason: 'CANOPY remains checker-backed coverage; ConCal recalibrates action values from shared continuations already in the batch'
  use_instead: method:canopy
- when: 'variable environment latency / async stragglers'
  reason: 'SAO remains async stragglers; ConCal is continuation-sharing credit'
  use_instead: method:sao
assumptions:
- 'GiGPO-style shared-state groups. Qwen2.5-1.5B-Instruct on ALFWorld/WebShop. Code: Yingjian-Chen/ConCal.'
last_reviewed: '2026-10-28'
papers:
- paper:concal
recipes:
- recipe:concal
claims:
- benchmark: 'ALFWorld and WebShop with Qwen2.5-1.5B-Instruct vs GiGPO'
  metric: 'success rate; within-group value-difference error'
  value: '+3.39 / +5.86 percentage points vs GiGPO on ALFWorld / WebShop; lower error in within-group value differences without extra rollouts'
  baseline: 'GiGPO single-continuation action values'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37195'
  notes: 'Does not retarget method:canopy.'
tags:
- rl-alignment
- agentic
- credit
- active
---

# ConCal

## Method Overview
ConCal matches visits from the same task by incoming state-action-state transitions, pools shared continuation evidence, and backup-calibrates earlier action values so credit is not hostage to one sampled suffix.

## When to Use
- Long-horizon agent RL that already groups shared states (GiGPO-style) and single-continuation values scramble local credit.

## When NOT to Use
Default on `task:outcome-only-long-horizon-agent-rl` remains `method:canopy`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy`.

## Gotchas & Failure Modes
- Not a replacement for `method:canopy`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
