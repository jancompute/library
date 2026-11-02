---
id: method:fair-cast
type: method
title: 'Fair Cast'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:fp4-rl-train-rollout-alignment'
  reason: 'TRACE / TRIAGE remain FP4 train-rollout first hops; Fair Cast is unbiased bf16 export of an fp32 master'
  use_instead: method:trace
- when: 'rounding-location alignment between inference and train (not export rounding)'
  reason: 'Rounding-Align RL matches where rounding happens; Fair Cast changes how the master is cast'
  use_instead: method:rounding-align-rl
assumptions:
- 'Split fp32-master / bf16-served RL. Official code andrewgcodes/faircast.'
last_reviewed: '2026-11-02'
papers:
- paper:fair-cast
recipes:
- recipe:fair-cast
claims:
- benchmark: 'Qwen3-0.6B to 4B RL, AdamW and Muon, 25 matched seed-pairs'
  metric: 'seed-pair wins / mean gain vs round-to-nearest export'
  value: '18 ahead / 6 tied / 1 behind; mean +6.1; zebra 0.57+/-0.16 vs 0.33+/-0.10'
  baseline: 'round-to-nearest fp32 to bf16 export; existing mismatch corrections that compare two post-round copies'
  date: '2026-11-02'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.41073'
  notes: 'Does not retarget method:trace. Distinct from method:rounding-align-rl and method:dlc.'
tags:
- rl
- numerics
- bf16
- active
---

# Fair Cast

## Method Overview
Fair Cast replaces round-to-nearest fp32-to-bf16 export with an unbiased rule (stochastic rounding or error feedback) and computes the RL loss on the served copy so per-step updates smaller than half a bf16 spacing are not discarded.

## When to Use
- RL that keeps an fp32 master and serves a bf16 copy, especially when only a tiny fraction of served weights change per step.

## When NOT to Use
Default on `task:fp4-rl-train-rollout-alignment` remains `method:trace`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:trace`. Distinct from `method:rounding-align-rl` (location) and `method:dlc` (discrepancy vs lag).

## Gotchas & Failure Modes
- Paper claims are dated 2026-11-02; no locked-SOTA bake-off.
- Round-to-nearest lag can act as a regularizer; restore it explicitly if a task needs it.
- Existing mismatch corrections cannot see this lag if they compare two copies downstream of the same rounding.
