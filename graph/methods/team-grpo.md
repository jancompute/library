---
id: method:team-grpo
type: method
title: 'Team-GRPO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; Team-GRPO is for group-dependent rewards'
  use_instead: method:cispo
- when: 'Pass@K / coverage / no-backward rather than Pass@1'
  reason: 'ES-reasoning remains Pass@K first hop'
  use_instead: method:es-reasoning
assumptions:
- 'Group-dependent rewards. Mention on task:passk-reasoning-coverage. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:team-grpo
recipes:
- recipe:team-grpo
claims:
- benchmark: 'GlobalOpinionQA; NoveltyBench'
  metric: 'opinion error / set utility vs GRPO'
  value: 'GlobalOpinionQA error 0.20 to 0.08; NoveltyBench avoids GRPO diversity collapse'
  baseline: 'GRPO / RLOO group-relative baseline (alpha=-1/(K-1))'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.02404'
  notes: 'Does not retarget method:cispo. Mention on task:passk-reasoning-coverage.'
tags:
- grpo
- diversity
- active
---

# Team-GRPO

## Method Overview
Team-GRPO keeps a group-relative form but flips the cross-term so diversity and coverage rewards are not turned into a zero-sum tournament.

## When to Use
- RLVR / preference rewards that depend on the rest of the group (diversity, coverage, distribution matching).

## When NOT to Use
CISPO remains Pass@1 with independent verifier rewards. ES-reasoning remains Pass@K coverage.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo` or `method:es-reasoning`.

## Gotchas & Failure Modes
- Only needed when the reward of a response depends on its groupmates.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
