---
id: method:self-steered-reasoner
type: method
title: 'Self-Steered Reasoner'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:privileged-teacher-opsd'
  reason: 'VISTA remains gold-teacher OPSD; SSR is reachability-aligned self-distill'
  use_instead: method:vista
assumptions:
- 'Privileged self-teacher with a reference solution. Distinct from method:ssr. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:self-steered-reasoner
recipes:
- recipe:self-steered-reasoner
claims:
- benchmark: 'pass@64=0 RL plateaus; AIME25/26+HMMT26'
  metric: 'recoverable trajectories / accuracy'
  value: '74.6% of pass@64=0 problems recovered; +4.9pp AIME25/26+HMMT26'
  baseline: 'privileged self-teacher without reachability projection; extensive RL'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.00796'
  notes: 'Does not retarget method:vista. Distinct from method:ssr.'
tags:
- opsd
- reachability
- active
---

# Self-Steered Reasoner

## Method Overview
SSR turns a privileged self-teacher into a directional signal over actions the unguided student can actually sample, then verifies and iterates.

## When to Use
- Privileged same-model self-distill where gold-conditioned traces look correct but are unreachable for the student.

## When NOT to Use
VISTA remains privileged-teacher OPSD. Do not confuse with method:ssr (harness scale racing).

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:vista`.

## Gotchas & Failure Modes
- Slug is self-steered-reasoner; method:ssr is successive scale racing.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
