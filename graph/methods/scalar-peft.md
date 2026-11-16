---
id: method:scalar-peft
type: method
title: SCALAR
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'single-adapter quality LoRA / rsLoRA + LR sweep rather than scalar PEFT'
    reason: 'Quality default remains vanilla LoRA + rsLoRA + LR sweep; SCALAR trains only layer-specific scalars over a frozen activation-derived basis'
    use_instead: method:lr-matters-lora
  - when: 'memory must fit a 4-bit PEFT stack'
    reason: 'AQLoRA-Q remains the 4-bit stack default; SCALAR is a scalar adapter, not a 4-bit recipe'
    use_instead: method:aqlora-q
assumptions:
  - 'Commonsense PEFT on Qwen2.5-7B / LLaMA3-8B. Activation-derived input basis plus a random output dictionary; only layer-specific scalars train. No public code as of 2026-11-16.'
last_reviewed: '2026-11-16'
papers:
- paper:scalar-peft
recipes:
- recipe:scalar-peft
claims:
- benchmark: 'Qwen2.5-7B / LLaMA3-8B commonsense PEFT vs LoRA r=8; 2x H20 peak mem and throughput'
  metric: 'accuracy; peak mem; throughput'
  value: 'Qwen2.5-7B 88.9 vs LoRA 88.8 at ~1/25 params; LLaMA3-8B 87.3 vs 87.4 at ~1/23; peak mem −20% vs LoRA; throughput +6%'
  baseline: 'LoRA r=8'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.17784'
  notes: 'Does not retarget method:lr-matters-lora. Mention on task:parameter-efficient-fine-tuning. code_status: none.'
tags:
- peft
- lora
- scalars
- active
---

# SCALAR

## Method Overview
SCALAR keeps a frozen, task-calibrated direction (activation-derived input basis plus a random output dictionary) and trains only layer-specific scalars. The claim is that PEFT quality lives in the direction more than in a learned low-rank magnitude.

## When to Use
- Commonsense PEFT when LoRA r=8 quality is enough and you want ~1/25 the trainable parameters plus a memory cut.

## When NOT to Use
Quality LoRA remains `method:lr-matters-lora`. 4-bit PEFT remains `method:aqlora-q`. Gate-projection deletion remains `method:deletion-tuning`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:lora-quality-tuning`. Mention on `task:parameter-efficient-fine-tuning`. Does **not** replace vanilla LoRA + rsLoRA + LR sweep.

## Gotchas & Failure Modes
- Matched LoRA r=8 on commonsense; not a bake-off against rsLoRA + LR sweep.
- No public trainer as of 2026-11-16 (`code_status: none`).
