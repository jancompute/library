---
id: method:c-mopd
type: method
title: 'C-MOPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked multi-teacher hop on task:student-distillation'
  reason: 'Open-MOPD remains token-share / gap-aware budget; C-MOPD is calibrated Top-K on a dynamic MoE'
  use_instead: method:open-mopd
assumptions:
- 'Dynamic MoE student plus independently optimized specialist teachers. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:c-mopd
recipes:
- recipe:c-mopd
claims:
- benchmark: 'Turing-20B-A2B four-domain specialist integration'
  metric: 'normalized integration score / retained specialist gain'
  value: '0.9988 overall; >=90.16% retained gain per domain; K=32 calibration 0.9962 vs 0.9724 / 0.9834 ablations'
  baseline: 'uncalibrated MOPD; no clipping; shared SFT; Qwen3-8B'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.39876'
  notes: 'Does not retarget method:open-mopd. Paper Open-MOPD is not the library 83.4% bake-off.'
tags:
- mopd
- moe
- active
---

# C-MOPD

## Method Overview
C-MOPD is the training piece of the Turing post-train writeup: calibrated Top-K on-policy distillation with per-teacher loss scale and clip, for folding independently trained specialists into one dynamically routed MoE. Serving tricks in the same paper are not this node.

## When to Use
- Dynamic-MoE post-train that must keep per-domain specialist gains instead of averaging them away.

## When NOT to Use
Open-MOPD remains the multi-teacher matching default (library 83.4% bake-off).

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:open-mopd` or `method:opd`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Paper Open-MOPD numbers are not the library 83.4% bake-off.
- Ignore the execution/dispatch half of the paper for this graph.
