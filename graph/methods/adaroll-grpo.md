---
id: method:adaroll-grpo
type: method
title: 'AdaRoll-GRPO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; AdaRoll-GRPO reallocates a fixed GRPO rollout budget with an offline BAMDP policy'
  use_instead: method:cispo
- when: 'adaptive sampling until at least one correct on math/code prompts (NGU)'
  reason: 'NGU keeps sampling online until a correct appears; AdaRoll learns an offline allocation policy'
  use_instead: method:ngu
assumptions:
- 'GRPO-family trainers with a fixed total rollout budget. Allocation policy computed offline. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:adaroll-grpo
recipes:
- recipe:adaroll-grpo
claims:
- benchmark: 'Multiple reasoning datasets and LLM architectures vs uniform GRPO rollouts'
  metric: 'training utility under a matched total rollout budget'
  value: 'consistently improves GRPO training performance under a fixed rollout budget'
  baseline: 'uniform per-question GRPO rollout allocation'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37429'
  notes: 'Does not retarget method:cispo.'
tags:
- rl-alignment
- rlvr
- allocation
- active
---

# AdaRoll-GRPO

## Method Overview
AdaRoll-GRPO treats per-question rollout allocation as a Bayes-adaptive MDP, learns the policy offline, and applies it during GRPO so hard prompts get enough positives without extra online optimization.

## When to Use
- GRPO-family math/code RL with a fixed rollout budget that is wasted on medium prompts and starved on hard ones.

## When NOT to Use
Default on `task:math-code-rl-dense` remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Not a replacement for `method:cispo`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
