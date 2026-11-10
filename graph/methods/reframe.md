---
id: method:reframe
type: method
title: 'Reframe (Observation-Aligned MOPD)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'choosing the multi-teacher distillation algorithm'
  reason: 'Open-MOPD remains text token-share / gap-aware budget; Reframe is observation-aligned VL MOPD'
  use_instead: method:open-mopd
- when: 'choosing the single-teacher distillation algorithm'
  reason: 'OPD remains matching; Reframe is multimodal teacher mix on a GD-GRPO host'
  use_instead: method:opd
assumptions:
- 'Vision-language student plus multimodal teachers that share the observation. Paper: Qwen3.5-9B image/video. Code EliYuan30/Reframe released as of 2026-11-10. Paper MOPD is not the library 83.4% bake-off. HF Daily leftover (cs.CV) ingested 2026-11-10. arXiv 2611.12886.'
last_reviewed: '2026-11-10'
papers:
- paper:reframe
recipes:
- recipe:reframe
claims:
- benchmark: 'Qwen3.5-9B image / video avg vs Mix-RL / MOPD'
  metric: 'accuracy'
  value: 'image 63.46→69.48 (+6.02), video 49.75→53.10 (+3.35) vs Mix-RL 66.75/51.41 and MOPD 68.19/52.32'
  baseline: 'Mix-RL / MOPD'
  date: '2026-11-10'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.12886'
  notes: 'Does not retarget method:open-mopd. Paper MOPD is not the library 83.4% bake-off. Code EliYuan30/Reframe.'
tags:
- distillation
- mopd
- vision
- grpo
- active
---

# Reframe (Observation-Aligned MOPD)

## Method Overview
Reframe runs GD-GRPO with OG-MOPD so multimodal teachers are mixed at the shared observation rather than at the text prompt alone.

## When to Use
- VL agent distillation when text-only MOPD teachers disagree because they saw different crops or frames.

## When NOT to Use
Text multi-teacher default remains `method:open-mopd`. Single-teacher matching remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Does **not** replace Open-MOPD.

## Gotchas & Failure Modes
- Paper MOPD numbers are not the library 83.4% bake-off.
- cs.CV leftover; ingested because it changes how a training agent mixes VL teachers, not because it retargets Open-MOPD.
