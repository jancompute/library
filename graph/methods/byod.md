---
id: method:byod
type: method
title: 'BYOD'
category: diffusion-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'recycle an AR post-training weight delta onto a converted dLLM'
  reason: 'A2D recycles a weight delta; BYOD is LoRA-only AR to masked DLM conversion'
  use_instead: method:a2d
- when: 'AR to discrete-dLLM on-policy distillation rather than LoRA conversion'
  reason: 'JustOPD distills AR logits on-policy; BYOD freezes the AR base and trains LoRA'
  use_instead: method:justopd
assumptions:
- 'Frozen AR checkpoint plus LoRA adapters. Official code RuurdKuiper/BYOD.'
last_reviewed: '2026-11-02'
papers:
- paper:byod
recipes:
- recipe:byod
claims:
- benchmark: 'Gemma 2 9B / Llama 3.1 8B / Qwen2.5 7B / Ministral 8B nine-task avg vs LLaDA 8B Instruct'
  metric: 'accuracy; conversion cost'
  value: 'BYOD-Gemma 50.6 vs LLaDA 51.9; 4.1-5.8% params; 3.1-4.0h Colab; <=102.4M tokens'
  baseline: 'LLaDA 8B Instruct; AR parents; A2D weight-delta; JustOPD'
  date: '2026-11-02'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.41574'
  notes: 'Does not retarget method:a2d. Open-gen PPL 8.3-11.1 vs LLaDA 4.1 is the remaining gap.'
tags:
- dllm
- lora
- active
---

# BYOD

## Method Overview
BYOD converts an AR LM into a masked diffusion LM with LoRA only: freeze every base parameter, train 4.1-5.8% adapters so the model can generate from fully masked sequences with bidirectional context.

## When to Use
- You already have an AR checkpoint and want a masked DLM without full-model fine-tune or A2D's weight-delta recycle.

## When NOT to Use
A2D remains AR-delta recycle. JustOPD remains on-policy AR-to-dLLM distill.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:a2d` or `method:justopd`.

## Gotchas & Failure Modes
- Open-generation quality at low NFE is the principal gap.
- Paper claims are dated 2026-11-02; no locked-SOTA bake-off.
