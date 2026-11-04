---
id: method:resi-math
type: method
title: 'ReSI-Math'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; ReSI-Math is a recoverable-frontier curriculum'
  use_instead: method:cispo
assumptions:
- 'Staged one-shot RLVR on recoverable items. Code released as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:resi-math
recipes:
- recipe:resi-math
claims:
- benchmark: 'Qwen3-VL-8B MATH500+WE-MATH'
  metric: 'accuracy after 3 one-shot RLVR stages / recoverable crossover'
  value: '78.71 to 80.16; crossover 272/621 (43.8%)'
  baseline: 'unadapted Qwen3-VL-8B'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.04787'
  notes: 'Does not retarget method:cispo. Distinct from method:fade / method:thinkprior.'
tags:
- rlvr
- math
- active
---

# ReSI-Math

## Method Overview
ReSI-Math ranks items by whether a short one-shot RLVR stage can recover them, then stages those recoverable frontiers.

## When to Use
- Dense math RLVR when most of the remaining error is recoverable with a short extra stage rather than a new loss.

## When NOT to Use
CISPO remains Pass@1. FADE / ThinkPrior remain schedulers of a different shape.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Curriculum, not a loss.
