---
id: method:coharl
type: method
title: 'CoHARL'
category: agents
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-harness-runtime'
  reason: 'omp2 remains the production harness kernel; CoHARL co-evolves a shared policy with a population of executable harnesses via RL'
  use_instead: method:omp2-harness
- when: 'alternating harness+policy optimization (Self-HPO)'
  reason: 'Self-HPO alternates one harness with the policy; CoHARL trains a harness population with a shared policy'
  use_instead: method:self-hpo
- when: 'issue-to-patch / locked eval'
  reason: 'mini-SWE-agent remains the SWE loop; CoHARL is harness-population RL'
  use_instead: task:software-engineering-agent-harness
assumptions:
- 'Population-based RL over executable harness code plus a shared policy. SWE-rebench / SWE-bench Verified / Terminal-Bench 2.0. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:coharl
recipes:
- recipe:coharl
claims:
- benchmark: 'SWE-rebench mean resolved; SWE-bench Verified; Terminal-Bench 2.0'
  metric: 'mean resolved rate vs harness-only search and matched-budget baselines'
  value: 'SWE-rebench 27.6% mean resolved, +6.4pp over harness-only search; beats search-once-then-RL and single-harness alternating updates at matched budget'
  baseline: 'harness-only search; search-once then RL; alternating single-harness revisions'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36469'
  notes: 'Does not retarget method:omp2-harness.'
tags:
- agents
- harness
- rl
- active
---

# CoHARL

## Method Overview
CoHARL co-evolves a shared policy and a population of executable harnesses. The policy learns from rollouts across the population; a proposer rewrites harness code from execution traces during training.

## When to Use
- You can edit the harness during policy RL and a single frozen harness (or one alternating rewrite) underfits the changing policy.

## When NOT to Use
Default on `task:agent-harness-runtime` remains `method:omp2-harness`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:omp2-harness`.

## Gotchas & Failure Modes
- Not a replacement for `method:omp2-harness`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
