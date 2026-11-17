---
id: method:sh-opd
type: method
title: SH-OPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains matching; SH-OPD samples a shared rollout horizon per batch'
    use_instead: method:opd
  - when: 'adaptive per-trajectory OPD rollout horizon via first-passage of low teacher-student compatibility'
    reason: 'Flash-OPD stops per sequence at a compatibility first-passage; SH-OPD uses one shared horizon per batch'
    use_instead: method:flash-opd
  - when: 'sparse OPD token budget (1-2 tokens per trajectory)'
    reason: 'sparse-opd-supervision keeps a few tokens; SH-OPD truncates sequence depth'
    use_instead: method:sparse-opd-supervision
assumptions:
  - 'Work in progress. Shared horizon per training batch for parallel generation. Math ~45% and code ~60% of full-OPD per-update cost. Code chen123CtrlS/SH-OPD. Distinct from method:flash-opd.'
last_reviewed: '2026-11-17'
papers:
- paper:sh-opd
recipes:
- recipe:sh-opd
claims:
- benchmark: 'mathematical reasoning and code generation vs full OPD'
  metric: 'accuracy; per-update cost'
  value: 'slightly higher math accuracy at ~45% of full-OPD per-update cost; competitive code at ~60% cost'
  baseline: 'standard full-horizon OPD'
  date: '2026-11-17'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.20687'
  notes: 'Work in progress. Does not retarget method:opd / method:flash-opd. Shared batch horizon, not per-sequence scheduling.'
tags:
- opd
- horizon
- efficiency
- active
---

# SH-OPD

## Method Overview
SH-OPD (Stochastic Horizons On-Policy Distillation) samples one shared horizon per training batch instead of supervising every token to the end. Parallel generation avoids per-sequence horizon scheduling. The paper characterizes the reweighting bias and a compute-reweighting trade-off.

## When to Use
- OPD when full-depth teacher matching is the per-update bottleneck and a shared truncated horizon is acceptable.

## When NOT to Use
Matching default remains `method:opd`. Per-sequence first-passage remains `method:flash-opd`. Token keep-masks remain `method:sparse-opd-supervision`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Does **not** replace OPD.

## Gotchas & Failure Modes
- Shared batch horizon is not per-sequence Flash-OPD.
- Comment: work in progress.
