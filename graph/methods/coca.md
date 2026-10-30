---
id: method:coca
type: method
title: 'CoCA'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'a programmatic checker exists and sparse outcome RL is enough'
  reason: 'CANOPY remains coverage; CoCA is capability-aware rubric co-evolution'
  use_instead: method:canopy
- when: 'reward-adaptive co-evolution of policy and rubric (RACE)'
  reason: 'RACE routes groups and switches phases; CoCA diagnoses criteria vs capability'
  use_instead: method:race-rubric
assumptions:
- 'Rubric-based open-ended RL. No programmatic checker required. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:coca
recipes:
- recipe:coca
claims:
- benchmark: 'open-ended rubric RL vs static / globally scheduled rubrics'
  metric: 'criterion difficulty vs policy capability'
  value: 'query-only vs rubric-guided diagnosis recalibrates mismatched criteria'
  baseline: 'static rubric; globally scheduled co-evolution'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.38566'
  notes: 'Does not retarget method:canopy or method:draco.'
tags:
- rubric
- rl
- active
---

# CoCA

## Method Overview
CoCA keeps the rubric on the policy's capability frontier. Query-only vs rubric-guided rollouts tell which criteria are already saturated, which are out of reach, and which just need guided exploration. Distinct from RACE's group-routing plus event-triggered rubric phases.

## When to Use
- Open-ended generation RL where a static rubric saturates or stays out of reach.

## When NOT to Use
Checker coverage remains CANOPY. Outcome-blind rubric first sibling remains DRACO.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy` or `method:draco`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Distinct from method:race-rubric (2610.40096).
- No public code as of 2026-10-30.
