---
id: method:race-rubric
type: method
title: 'RACE'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'a programmatic checker exists and sparse outcome RL is enough'
  reason: 'CANOPY remains coverage; RACE is reward-adaptive rubric co-evolution'
  use_instead: method:canopy
- when: 'capability-aware policy+rubric co-evolution (CoCA)'
  reason: 'CoCA diagnoses criteria vs capability; RACE routes groups and switches phases'
  use_instead: method:coca
assumptions:
- 'Group rubric RL. Event-triggered phase switch. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:race-rubric
recipes:
- recipe:race-rubric
claims:
- benchmark: 'open-ended rubric RL vs globally scheduled co-evolution'
  metric: 'group informativeness / phase switching'
  value: 'policy updates only on informative groups; rubric phase on saturation'
  baseline: 'static rubric; globally prescribed update schedule'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.40096'
  notes: 'Does not retarget method:canopy or method:coca.'
tags:
- rubric
- rl
- active
---

# RACE

## Method Overview
RACE co-evolves policy and rubric by the informativeness of the current reward, not a calendar. Informative groups train the policy; collapsed groups are skipped; rubric-failed groups wait for a rubric phase that starts on saturation and stops on plateau.

## When to Use
- Rubric RL where some groups are already uninformative and a global rubric schedule wastes updates.

## When NOT to Use
CANOPY/DRACO remain the outcome-only hops. CoCA is the capability-aware criterion sibling.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy`, `method:draco`, or `method:coca`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Distinct from method:coca (2610.38566).
- No public code as of 2026-10-30.
