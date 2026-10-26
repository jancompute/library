---
id: method:frontier-opd
type: method
title: 'Frontier-OPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:student-distillation'
  reason: 'OPD remains matching; Frontier-OPD supervises only decision states on the student''s learning frontier'
  use_instead: method:opd
- when: 'outcome-only long-horizon agent RL (CANOPY)'
  reason: 'CANOPY remains coverage RL; Frontier-OPD is teacher OPD at the student''s edge'
  use_instead: method:canopy
assumptions:
- 'Multi-turn agents. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:frontier-opd
recipes:
- recipe:frontier-opd
claims:
- benchmark: 'Multi-turn agent OPD vs full-trajectory teacher matching'
  metric: 'useful teacher supervision at states the student can still sustain'
  value: 'teaches at the student''s learning frontier rather than matching every turn'
  baseline: 'vanilla OPD on full agent traces'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32802'
  notes: 'Does not retarget method:opd.'
tags:
- distillation
- agents
- active
---

# Frontier-OPD

## Method Overview
Frontier-OPD finds decision states that are still hard but recoverable and spends teacher OPD there instead of matching the whole trajectory.

## When to Use
- Multi-turn agent distill where most turns are already easy and full-trace OPD wastes teacher budget.

## When NOT to Use
Default on `task:student-distillation` remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Not a replacement for `method:opd`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
