---
id: method:ngramrl
type: method
title: 'NgramRL'
category: training-systems
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:frontier-rl-posttrain-stack'
  reason: 'Miles remains the production engine; NgramRL is a model-free n-gram drafter for structured RL rollouts'
  use_instead: method:miles
- when: 'lossless multi-token / diffusion-augmented AR serving (Uno)'
  reason: 'Uno remains serving; NgramRL is an RL-rollout n-gram drafter'
  use_instead: method:uno
assumptions:
- 'Structured generation RL where rollouts dominate wall-clock. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:ngramrl
recipes:
- recipe:ngramrl
claims:
- benchmark: 'RL post-train rollout time vs autoregressive decode / model-based speculative decoding'
  metric: 'rollout wall-clock share of RL post-training'
  value: 'rollout-aware n-gram speculative decoding without a learned draft model that drifts with the policy'
  baseline: 'AR rollouts; model-based speculative decoding; Uno diffusion-augmented AR'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32881'
  notes: 'Does not retarget method:miles.'
tags:
- rl
- speculative-decoding
- active
---

# NgramRL

## Method Overview
NgramRL speeds structured-generation RL rollouts with a rollout-aware n-gram drafter so you do not keep a learned draft model that drifts as the policy moves.

## When to Use
- RL post-train whose time is mostly structured rollouts and a learned drafter would go stale.

## When NOT to Use
Default on `task:frontier-rl-posttrain-stack` remains `method:miles`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:miles`.

## Gotchas & Failure Modes
- Not a replacement for `method:miles`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
