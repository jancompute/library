---
id: method:sama
type: method
title: 'SaMA'
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:lora-quality-tuning'
  reason: 'Vanilla LoRA + rsLoRA + LR sweep remains quality default; SaMA is Kronecker PEFT'
  use_instead: method:lr-matters-lora
assumptions:
- 'NeurIPS 2026 Kronecker adapter. Mention on task:parameter-efficient-fine-tuning. No public code as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:sama
recipes:
- recipe:sama
claims:
- benchmark: 'matched-parameter PEFT rank'
  metric: 'effective rank vs LoRA'
  value: 'quadratic rank vs LoRA at matched parameter budget'
  baseline: 'vanilla LoRA'
  date: '2026-11-04'
  verified: true
  evidence_level: peer-reviewed
  source_url: 'https://arxiv.org/abs/2611.04462'
  notes: 'NeurIPS 2026. Does not retarget method:lr-matters-lora.'
tags:
- peft
- lora
- active
---

# SaMA

## Method Overview
SaMA replaces LoRA's two thin factors with a Kronecker factorization so effective rank grows quadratically at a matched parameter budget.

## When to Use
- PEFT when LoRA rank saturates and a Kronecker adapter is acceptable.

## When NOT to Use
Vanilla LoRA + rsLoRA + LR sweep remains the 24GB quality default.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:lr-matters-lora`.

## Gotchas & Failure Modes
- No public code as of 2026-11-04.
- Not a LoRA LR-sweep bake-off.
