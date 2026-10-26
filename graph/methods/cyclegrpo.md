---
id: method:cyclegrpo
type: method
title: 'CycleGRPO'
category: multimodal-rl
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:mllm-finegrained-perception-rl'
  reason: 'Vision-RL2 remains region-proposal RL; CycleGRPO couples understand and localize across spatial/temporal domains'
  use_instead: method:vision-rl2
assumptions:
- 'Fine-grained multimodal RL. Code devinxzhang/CycleGRPO.'
last_reviewed: '2026-10-26'
papers:
- paper:cyclegrpo
recipes:
- recipe:cyclegrpo
claims:
- benchmark: 'Fine-grained multimodal understand+ground vs separate-objective RL'
  metric: 'joint region understanding and localization'
  value: 'one GRPO-style loop coupling understand and localize across spatial, temporal, and spatio-temporal domains'
  baseline: 'separate understand / localize objectives; Vision-RL2 RoI RL'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.29552'
  notes: 'Does not retarget method:vision-rl2.'
tags:
- multimodal-rl
- grounding
- active
---

# CycleGRPO

## Method Overview
CycleGRPO is unified RL that couples region understanding and localization instead of training those directions with separate objectives.

## When to Use
- MLLM grounding where understand-only or localize-only RL leaves the other skill behind.

## When NOT to Use
Default on `task:mllm-finegrained-perception-rl` remains `method:vision-rl2`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:vision-rl2`.

## Gotchas & Failure Modes
- Not a replacement for `method:vision-rl2`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
