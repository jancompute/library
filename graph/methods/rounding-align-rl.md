---
id: method:rounding-align-rl
type: method
title: 'Rounding-Align RL'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:fp4-rl-train-rollout-alignment'
  reason: 'TRACE / TRIAGE remain FP4 train-rollout first hops; this card aligns where BF16 rounding happens across inference and train'
  use_instead: method:trace
- when: 'direction-aware NVFP4 mismatch (TRIAGE)'
  reason: 'TRIAGE is NVFP4; this card is BF16 rounding location'
  use_instead: method:triage
assumptions:
- 'Split inference/train RL stacks in BF16. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:rounding-align-rl
recipes:
- recipe:rounding-align-rl
claims:
- benchmark: 'Split inference/train LLM RL vs aligning rounding location only'
  metric: 'on-policy-ness of an intended on-policy RL update under BF16 stack mismatch'
  value: 'aligning where rounding happens stabilizes RL without matching the whole inference/train stack'
  baseline: 'unaligned BF16 inference vs train; full-stack alignment; TRACE / TRIAGE NVFP4'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32951'
  notes: 'Does not retarget method:trace.'
tags:
- rl
- numerics
- active
---

# Rounding-Align RL

## Method Overview
Even identical BF16 weights can make intended on-policy RL off-policy when inference and train round in different places. This card aligns rounding location only.

## When to Use
- Disaggregated RL where you cannot unify the whole stack but can match rounding sites.

## When NOT to Use
Default on `task:fp4-rl-train-rollout-alignment` remains `method:trace`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:trace`.

## Gotchas & Failure Modes
- Not a replacement for `method:trace`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
