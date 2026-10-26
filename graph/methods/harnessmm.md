---
id: method:harnessmm
type: method
title: 'HarnessMM'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-harness-runtime'
  reason: 'omp2 remains the production kernel; HarnessMM reuses earlier tool-loop decisions and RSI-edits a companion harness'
  use_instead: method:omp2-harness
assumptions:
- 'Tool-loop harness that re-invokes reasoning after tool feedback. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:harnessmm
recipes:
- recipe:harnessmm
claims:
- benchmark: 'Agent harness token use vs re-reasoning after every tool observation'
  metric: 'tokens spent re-invoking reasoning after tool feedback'
  value: 'guarded decision reuse plus RSI of a companion harness vs re-thinking after every tool result'
  baseline: 'omp2-style kernel with naive post-tool re-reason'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32813'
  notes: 'Does not retarget method:omp2-harness.'
tags:
- agent-harness
- rsi
- active
---

# HarnessMM

## Method Overview
HarnessMM stops re-invoking reasoning after every tool observation when an earlier call already fixed the next action, and RSI-refines a companion harness.

## When to Use
- Tool-using harnesses whose token bill is dominated by redundant post-tool re-reasoning.

## When NOT to Use
Default on `task:agent-harness-runtime` remains `method:omp2-harness`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:omp2-harness`.

## Gotchas & Failure Modes
- Not a replacement for `method:omp2-harness`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
