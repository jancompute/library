---
id: method:harnessflow
type: method
title: 'HarnessFlow'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-harness-runtime'
  reason: 'omp2 remains the production kernel; HarnessFlow is MCTS full-harness search'
  use_instead: method:omp2-harness
assumptions:
- 'Model and task environment held fixed. 15 refinements per benchmark. Sibling of ParetoSaddler / ActiveSaddler. No dedicated GitHub as of 2026-11-05.'
last_reviewed: '2026-11-05'
papers:
- paper:harnessflow
recipes:
- recipe:harnessflow
claims:
- benchmark: 'TAU2 / AppWorld / BigCodeBench-Hard / SWE-bench Verified / WebShop / BrowseComp-Plus'
  metric: 'mean test score; per-task cost vs Codex'
  value: '69.48% mean (+10.89 vanilla / +3.95 Meta-Harness); 41.4% of Codex cost'
  baseline: 'vanilla harness / Meta-Harness / hand-engineered baselines'
  date: '2026-11-05'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.06254'
  notes: '15 refinements; mean best-so-far validation 71.5% after 3 evals, 74.2% by round 15. Does not retarget method:omp2-harness.'
tags:
- agent-harness
- mcts
- rsi
- active
---

# HarnessFlow

## Method Overview
HarnessFlow searches over complete executable harnesses with the model and environment frozen. Candidates live in a refinement tree. An MCTS policy picks which harness to edit next; a coding agent applies the edit using archived code, traces, and a reusable harness-component library.

## When to Use
- Automating full-harness code search under a small candidate-evaluation budget, when ParetoSaddler / ActiveSaddler are not already covering the search.

## When NOT to Use
omp2 remains the production kernel. Issue-to-patch ranking stays mini-SWE-agent. Weight post-train stays NeoHorse-1 / SAO.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:omp2-harness`. Sibling of `method:paretosaddler` and `method:activesaddler`.

## Gotchas & Failure Modes
- Search is over harness code, not policy weights.
- No dedicated public repo as of 2026-11-05.
