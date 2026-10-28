---
id: method:duplextune
type: method
title: 'DuplexTune'
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:full-param-memory-efficient-pretrain'
  reason: 'SCALE remains full-param memory-efficient pretrain; DuplexTune replays coupled hidden states through frozen MoE modules with width bridges'
  use_instead: method:scale
- when: 'quality LoRA on 24GB without a fully quantized checkpoint constraint'
  reason: 'Vanilla LoRA + rsLoRA + LR sweep remains dense quality PEFT; DuplexTune is MoE coupled-state replay'
  use_instead: method:lr-matters-lora
- when: 'MoE PEFT adapter consolidation (ACE)'
  reason: 'ACE consolidates expert adapters; DuplexTune replays coupled residual streams'
  use_instead: method:ace-moe-peft
assumptions:
- 'Qwen1.5-MoE-A2.7B, single H800, frozen router, bridge warm-up then backbone. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:duplextune
recipes:
- recipe:duplextune
claims:
- benchmark: 'Qwen1.5-MoE-A2.7B single-H800 vs checkpointed SFT'
  metric: 'peak memory; throughput; MMLU / GSM8K / MT-Bench'
  value: '38.8 GB peak vs 64.8 GB checkpointed SFT; 25.1 vs 19.9 samples/s; 67.2% MMLU, 75.6% GSM8K, 7.69 MT-Bench (weaker multilingual than the checkpointed baseline)'
  baseline: 'supervised fine-tuning with activation checkpointing'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36009'
  notes: 'Does not retarget method:scale.'
tags:
- peft
- moe
- memory
- active
---

# DuplexTune

## Method Overview
DuplexTune replays coupled hidden states through pretrained attention and expert modules via trainable width bridges on two residual streams. Bridges warm up first; the router stays frozen.

## When to Use
- MoE adaptation where stored activations dominate memory even though experts are sparse, and a mixed multilingual regression is acceptable.

## When NOT to Use
Default on `task:full-param-memory-efficient-pretrain` remains `method:scale`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:scale`.

## Gotchas & Failure Modes
- Not a replacement for `method:scale`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
