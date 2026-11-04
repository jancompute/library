---
id: method:moeresq
type: method
title: 'MoeResQ'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:fp4-rl-train-rollout-alignment'
  reason: 'TRACE / TRIAGE remain dual-active; MoeResQ is residual-corrected FP4 MoE RL'
  use_instead: method:trace
assumptions:
- 'MoE RL with simulated HiF4 experts; routers stay BF16. No public code as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:moeresq
recipes:
- recipe:moeresq
claims:
- benchmark: 'Qwen3-30B-A3B GRPO DAPO-Math'
  metric: 'AMC23 / AIME24 / AIME25 / MATH500 vs BF16 and HiF4'
  value: 'MoeResQ AMC23 84.45 vs BF16 85.10 vs HiF4 65.23 vs RolloutResQ 62.34; experts-only 84.61 / 46.98 / 32.92 / 86.17'
  baseline: 'BF16 GRPO; HiF4; rollout-only residual correction'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.04376'
  notes: 'Does not retarget method:trace / method:triage. Simulated HiF4; routers BF16.'
tags:
- quantization
- fp4
- moe
- active
---

# MoeResQ

## Method Overview
MoeResQ keeps a residual correction on both the train-side and rollout-side FP4 expert path so MoE RL does not drift off the BF16 policy.

## When to Use
- Native or simulated FP4 MoE RL where rollout-only quantization tanks math RLVR.

## When NOT to Use
TRACE / TRIAGE remain the dual-active first hops for NVFP4 train–rollout mismatch. Quartet-II remains native FP4 pretrain.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:trace` or `method:triage`.

## Gotchas & Failure Modes
- Simulated HiF4, not a native NVFP4 bake-off against TRACE.
- Routers stay BF16 (0.041% of params).
- No public code as of 2026-11-04.
