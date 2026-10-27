---
id: method:s3ac
type: method
title: 'S3AC'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:token-level-critic-rl'
  reason: 'BPCO remains the single-sample critic default; S3AC is a long-CoT critic plus DAPS prompt sampler'
  use_instead: method:bpco
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; S3AC is a critic recipe, not the CISPO loss'
  use_instead: method:cispo
assumptions:
- 'Long-CoT RLVR critic. Token advantages plus DAPS. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:s3ac
recipes:
- recipe:s3ac
claims:
- benchmark: 'Long-CoT RLVR critic vs GRPO-X / critic-free single-rollout'
  metric: 'group-rollout quality; 35B single-rollout stability'
  value: 'beats GRPO-X on dense and MoE 1.5B-397B; 35B single-rollout holds while critic-free baselines fade'
  baseline: 'GRPO-X; critic-free grouped RLVR'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.35518'
  notes: 'Does not retarget method:bpco or method:cispo.'
tags:
- rl-alignment
- actor-critic
- active
---

# S3AC

## Method Overview
S3AC trains a long-CoT critic for token advantages and prompt baselines, then samples prompts by estimated difficulty so rollouts are not spent on already-easy items.

## When to Use
- Token-level critic RL on long CoT where group baselines waste samples and a naive value head is unstable.

## When NOT to Use
Default on `task:token-level-critic-rl` remains `method:bpco`. Pass@1 remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:bpco`.

## Gotchas & Failure Modes
- Not a replacement for `method:bpco` or `method:cispo`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
