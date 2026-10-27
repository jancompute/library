---
id: method:fork-precision
type: method
title: 'FORK (Precision Objective)'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:outcome-only-long-horizon-agent-rl when a checker exists'
  reason: 'CANOPY remains checker coverage; FORK is a rubric precision objective against coverage-only verbosity'
  use_instead: method:canopy
- when: 'outcome-blind rubric credit when no checker exists'
  reason: 'DRACO remains the rubric sibling; FORK adds precision/necessity credits on a rubric host'
  use_instead: method:draco
- when: 'dLLM RL that forks from high-entropy intermediate states (ForkGRPO)'
  reason: 'ForkGRPO is dLLM rollout forking; FORK here is a rubric precision reward, not that trainer'
  use_instead: method:forkgrpo
assumptions:
- 'Rubric RL with recall plus precision. Distinct from method:forkgrpo. No public code as of 2026-10-27. HF Daily 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:fork-precision
recipes:
- recipe:fork-precision
claims:
- benchmark: 'Rubric RL vs coverage-only weighted rubric rewards'
  metric: 'completeness vs precision / preference vs verbosity'
  value: 'joint recall+precision beats coverage-only rubric RL; Pareto on completeness vs unnecessary content'
  baseline: 'coverage-weighted rubric RL / DRACO-style rubric credit'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.33512'
  notes: 'Does not retarget method:canopy, method:draco, or method:forkgrpo.'
tags:
- rl-alignment
- rubric
- active
---

# FORK (Precision Objective)

## Method Overview
FORK scores each response unit for necessity and factual correctness so rubric RL does not maximize coverage by dumping extra, wrong, or unused content.

## When to Use
- Rubric-based RL where coverage rewards make answers longer and less preferred than the base model.

## When NOT to Use
Checker coverage remains `method:canopy`. Outcome-blind rubrics remain `method:draco`. Not `method:forkgrpo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy` or `method:draco`. Distinct from `method:forkgrpo`.

## Gotchas & Failure Modes
- Name collision: not `method:forkgrpo`.
- Not a replacement for `method:canopy` or `method:draco`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
