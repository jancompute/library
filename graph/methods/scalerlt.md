---
id: method:scalerlt
type: method
title: 'ScaleRLT'
category: training-systems
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:recurrent-encoder-decoder-lm'
  reason: 'RLT remains the experimental CED architecture; ScaleRLT is exact logp for deferred looped rollouts'
  use_instead: method:recurrent-looped-transformer
- when: 'Huginn-style dense fixed-point looped LMs'
  reason: 'Looped Models Done Right is the Huginn recipe; ScaleRLT is the RL logp/rollout numeric fix'
  use_instead: method:looped-models-done-right
assumptions:
- 'Looped-transformer RL numerics. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:scalerlt
recipes:
- recipe:scalerlt
claims:
- benchmark: 'Looped-transformer GRPO logp vs dense learner / deferred rollout'
  metric: 'same-weight token gate; rollout throughput; GRPO loss vs float64'
  value: 'bit-exact replay in 167 FP32 and 28 bf16 cells; 1.47-1.56x one-GPU deferral; GRPO loss 3.1e-4 vs float64'
  baseline: 'dense learner logp vs deferred schedule without hybrid replay'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.34427'
  notes: 'Does not retarget method:recurrent-looped-transformer.'
tags:
- looped-lm
- rlvr
- active
---

# ScaleRLT

## Method Overview
ScaleRLT sets learner log-probability to dense-forward plus a stop-gradient of (schedule replay minus dense), so the value matches the deferred rollout bit for bit and the gradient stays the dense learner.

## When to Use
- On-policy RL on looped transformers that defer deep loops at rollout time.

## When NOT to Use
Default on `task:recurrent-encoder-decoder-lm` remains `method:recurrent-looped-transformer`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:recurrent-looped-transformer`.

## Gotchas & Failure Modes
- Not a replacement for `method:recurrent-looped-transformer`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
