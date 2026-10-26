---
id: method:rsihub
type: method
title: 'RSIHub'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-harness-runtime'
  reason: 'omp2 remains the production kernel; RSIHub is shared infrastructure for RSI recipes, not the kernel'
  use_instead: method:omp2-harness
assumptions:
- 'Harness RSI research. Code simple-agent-lab/RSIHub.'
last_reviewed: '2026-10-26'
papers:
- paper:rsihub
recipes:
- recipe:rsihub
claims:
- benchmark: 'Agent-evolution method comparison on shared operators / mutable resources'
  metric: 'whether RSI recipes can share execution, evaluation, and resources'
  value: 'composable operators plus declared mutable resources vs rebuilding RSI machinery per paper'
  baseline: 'one-off RSI implementations; omp2 production kernel'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32253'
  notes: 'Does not retarget method:omp2-harness.'
tags:
- agent-harness
- rsi
- active
---

# RSIHub

## Method Overview
RSIHub is shared infrastructure for agent-evolution methods: recipes compose operators and declare what they may mutate.

## When to Use
- Comparing or extending harness-RSI methods without forking a new runtime each time.

## When NOT to Use
Default on `task:agent-harness-runtime` remains `method:omp2-harness`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:omp2-harness`.

## Gotchas & Failure Modes
- Not a replacement for `method:omp2-harness`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
