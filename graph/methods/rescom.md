---
id: method:rescom
type: method
title: 'ResCom'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:fp4-hardware-training'
  reason: 'Quartet-II remains native FP4 training; ResCom is a closed-form activation-residual PTQ correction after calibration'
  use_instead: method:quartet-ii
- when: 'dual-scale calibration-free W+A PTQ for AR LLMs (DualQuant)'
  reason: 'DualQuant is dual-scale reconstruction; ResCom is low-rank residual compensation on rounding error'
  use_instead: method:dualquant
assumptions:
- 'Post-training W+A quantization with a calibrated checkpoint. Closed-form, no gradient. Llama-3-8B W4A4. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:rescom
recipes:
- recipe:rescom
claims:
- benchmark: 'Llama-3-8B W4A4 WikiText-2 / MMLU / five-shot GSM8K'
  metric: 'perplexity; MMLU; GSM8K accuracy'
  value: 'rank-32 attention corrections: WikiText-2 PPL 7.708 to 7.147, MMLU +2.89pp, GSM8K 23.96 to 36.16'
  baseline: 'calibrated W4A4 without residual compensation'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.35955'
  notes: 'Does not retarget method:quartet-ii.'
tags:
- quantization
- ptq
- active
---

# ResCom

## Method Overview
ResCom stores a low-rank correction driven by the activation rounding residual so reconstructions can tell activations in the same quantization bin apart. Directions are chosen by output-aware calibration and the correction is closed-form.

## When to Use
- W4A4 / low-bit W+A PTQ where calibration already ran and activation rounding still collapses bins.

## When NOT to Use
Default on `task:fp4-hardware-training` remains `method:quartet-ii`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:quartet-ii`.

## Gotchas & Failure Modes
- Not a replacement for `method:quartet-ii`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
