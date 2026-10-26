---
id: method:ms-ttrl
type: method
title: 'MS-TTRL'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:label-free-test-time-reasoner'
  reason: 'TTPO remains the unlabeled TTT first hop; MS-TTRL is TTRL when several answers are valid and frequency fights diversity'
  use_instead: method:ttpo
assumptions:
- 'Unlabeled test instances with multiple valid solutions. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:ms-ttrl
recipes:
- recipe:ms-ttrl
claims:
- benchmark: 'Multiple-solution TTRL vs frequency-as-reward majority vote'
  metric: 'coverage of valid solutions vs collapse onto the mode'
  value: 'breaks the conflict where generation frequency is both the reward and the thing you do not want to collapse'
  baseline: 'majority-vote TTRL / TTPO-style consensus'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32234'
  notes: 'Does not retarget method:ttpo.'
tags:
- ttt
- ttrl
- active
---

# MS-TTRL

## Method Overview
MS-TTRL is test-time RL for tasks with several valid solutions, where using generation frequency as reward collapses the solution set.

## When to Use
- Label-free TTT on problems that admit many valid answers and majority vote erases them.

## When NOT to Use
Default on `task:label-free-test-time-reasoner` remains `method:ttpo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:ttpo`.

## Gotchas & Failure Modes
- Not a replacement for `method:ttpo`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
