---
id: method:proland
type: method
title: 'ProLand'
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:lora-quality-tuning'
  reason: 'Vanilla LoRA + rsLoRA + LR sweep remains the 24GB quality default'
  use_instead: method:lr-matters-lora
- when: 'memory must fit a 4-bit PEFT stack'
  reason: 'AQLoRA-Q remains 4-bit PEFT; ProLand is a full-precision manifold LoRA optimizer'
  use_instead: method:aqlora-q
assumptions:
- 'LoRA adapters with a Stiefel basis constraint. Encoder GLUE and 3B–16B-A3B decoder ranks. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:proland
recipes:
- recipe:proland
claims:
- benchmark: '11 GLUE/decoder tasks, DeBERTa-v3-base / Qwen2.5-3B / Llama-3.2-3B / Moonlight-16B-A3B'
  metric: 'average score vs compared LoRA optimizers'
  value: 'highest average in every tested encoder and decoder model-rank configuration'
  baseline: 'compared LoRA / manifold methods in the paper'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.00236'
  notes: 'Does not retarget method:lr-matters-lora. Mention on task:parameter-efficient-fine-tuning.'
tags:
- peft
- lora
- muon
- active
---

# ProLand

## Method Overview
ProLand fine-tunes LoRA by landing on the Stiefel manifold without retractions, using coordinated factor updates and Muon-style spectral steps on the represented weight increment.

## When to Use
- Quality LoRA where orthonormal bases matter and a Muon-family direction is acceptable.

## When NOT to Use
Vanilla LoRA + rsLoRA + LR sweep remains the 24GB quality default. AQLoRA-Q remains 4-bit PEFT.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:lr-matters-lora` or `method:aqlora-q`.

## Gotchas & Failure Modes
- No public code as of 2026-11-03.
- Not a bake-off against the library rsLoRA + LR-sweep default.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
