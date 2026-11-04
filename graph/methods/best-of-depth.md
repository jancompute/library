---
id: method:best-of-depth
type: method
title: 'Best-of-Depth'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the first hop on task:elastic-depth-looped-lm'
  reason: 'ELR remains mixed-depth elastic recurrence; Best-of-Depth supervises all depths as candidates'
  use_instead: method:elr
assumptions:
- 'Looped LM coverage training. No public code as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:best-of-depth
recipes:
- recipe:best-of-depth
claims:
- benchmark: 'N-Queens coverage'
  metric: 'success vs final-depth training'
  value: '91.03% vs 45.75% final-depth'
  baseline: 'supervise only the last loop'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.04663'
  notes: 'Does not retarget method:elr.'
tags:
- architecture
- looped-lm
- active
---

# Best-of-Depth

## Method Overview
Best-of-Depth trains every loop count as a candidate so decode can pick a depth that actually solved the instance.

## When to Use
- Elastic-depth looped LMs where final-depth supervision hides solutions found at earlier loops.

## When NOT to Use
ELR remains the mixed-depth first hop. Dory is a separate nGPT 4B recipe.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:elr`.

## Gotchas & Failure Modes
- Coverage metric, not a 4B/30B-A3B ELR bake-off.
- No public code as of 2026-11-04.
