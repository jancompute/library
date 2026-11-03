---
id: method:swe-trail
type: method
title: 'SWE-Trail'
category: training-systems
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:coding-agent-rl-environment-construction'
  reason: 'CodeMidas remains source-code env construction; SWE-Trail is trajectory collection'
  use_instead: method:codemidas
assumptions:
- 'History-guided SWE trajectory collection then student training. 124B student. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:swe-trail
recipes:
- recipe:swe-trail
claims:
- benchmark: 'SWE-bench Multilingual / Pro, 124B student'
  metric: 'resolved pp vs independent sampling'
  value: '+2.33 / +1.60 pp'
  baseline: 'independent multi-sample trajectory collection'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.02074'
  notes: 'Does not retarget method:codemidas.'
tags:
- swe
- trajectories
- active
---

# SWE-Trail

## Method Overview
SWE-Trail spends extra collection budget at history-chosen checkpoints while the coding agent still sees only its ordinary context, avoiding advice leakage at train time.

## When to Use
- Collecting SWE post-train trajectories where independent sampling is redundant.

## When NOT to Use
CodeMidas remains source-code env construction. mini-SWE-agent remains issue-to-patch.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:codemidas` or `method:mini-swe-agent`.

## Gotchas & Failure Modes
- Collection method, not a SWE harness ranking.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
