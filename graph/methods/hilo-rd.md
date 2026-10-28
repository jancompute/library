---
id: method:hilo-rd
type: method
title: 'HiLo-RD'
category: diffusion
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:diffusion-lm-ar-delta-recycle'
  reason: 'A2D remains AR-delta recycle; HiLo-RD distills large-window teacher states onto cropped small-window views of the same masked dLLM'
  use_instead: method:a2d
- when: 'AR to discrete-dLLM on-policy distillation (JustOPD)'
  reason: 'JustOPD distills an AR teacher into a dLLM; HiLo-RD is same-model cross-budget hidden-state matching'
  use_instead: method:justopd
- when: 'masked dLLM lookahead-edit SFT (LED)'
  reason: 'LED edits commitments; HiLo-RD matches hidden states across generation budgets'
  use_instead: method:led
assumptions:
- 'Masked dLLMs (MDLM) with a larger teacher window. No external teacher. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:hilo-rd
recipes:
- recipe:hilo-rd
claims:
- benchmark: 'Mathematics benches under a limited generation budget; GSM8K; code transfer without code-domain training'
  metric: 'low-budget accuracy; mean readable length'
  value: 'GSM8K +9.4 percentage points as mean readable length falls about 25%; low-budget math gains transfer to code generation'
  baseline: 'same MDLM without cross-budget hidden-state distillation'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36901'
  notes: 'Does not retarget method:a2d.'
tags:
- diffusion
- dllm
- distillation
- active
---

# HiLo-RD

## Method Overview
HiLo-RD pairs large-window teacher states with cropped small-window views and matches hidden representations at committed positions so the model does not freeze answer fragments at the window boundary before reasoning finishes.

## When to Use
- Masked dLLM decoding under a tight generation budget that commits answer tokens too early.

## When NOT to Use
Default on `task:diffusion-lm-ar-delta-recycle` remains `method:a2d`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:a2d`.

## Gotchas & Failure Modes
- Not a replacement for `method:a2d`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
