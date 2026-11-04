---
id: method:meta2
type: method
title: 'Meta2'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-harness-runtime'
  reason: 'omp2 remains the production kernel; Meta2 is online KEEP/EVOLVE control'
  use_instead: method:omp2-harness
assumptions:
- 'Frozen-weight harness control on GPT-5.6-Terra. No public code as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:meta2
recipes:
- recipe:meta2
claims:
- benchmark: 'Terminal-Bench 2.1 / DeepSWE 1.1'
  metric: 'success with GPT-5.6-Terra'
  value: 'TB2.1 81.00%; DeepSWE 1.1 44.44%'
  baseline: 'static harness'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.05139'
  notes: 'Does not retarget method:omp2-harness. Not a SWE-bench paper-protocol ranking of mini-SWE-agent.'
tags:
- agent-harness
- rsi
- active
---

# Meta2

## Method Overview
Meta2 is an online KEEP/EVOLVE controller that rewrites harness skills only when the live run says the current skill is failing.

## When to Use
- Production-style harness RSI where you need a KEEP/EVOLVE gate rather than unconditional rewrite.

## When NOT to Use
omp2 remains the production kernel. ParetoSaddler remains quality+cost search. mini-SWE-agent remains issue-to-patch.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:omp2-harness`.

## Gotchas & Failure Modes
- Numbers are on GPT-5.6-Terra, not a trained policy.
- No public code as of 2026-11-04.
