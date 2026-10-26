---
id: method:lazyflash
type: method
title: 'LazyFlash'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:posttrain-attention-sparsification'
  reason: 'SAS remains gated inference/train sparsification; LazyFlash keeps a dense forward and sparsifies the backward for long-context FT'
  use_instead: method:sas
assumptions:
- 'Long-context FT where attention is the train bottleneck. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:lazyflash
recipes:
- recipe:lazyflash
claims:
- benchmark: 'Long-context FT vs dense FlashAttention / inference-only sparse attention'
  metric: 'wall-clock of long-context fine-tuning'
  value: 'dense forward + sparse backward attention vs training dense because inference sparsity does not speed the backward'
  baseline: 'dense FlashAttention FT; inference-only sparse attention'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.31911'
  notes: 'Does not retarget method:sas.'
tags:
- sparse-attention
- finetune
- active
---

# LazyFlash

## Method Overview
LazyFlash keeps a dense attention forward pass and sparsifies the backward so long-context fine-tuning gets a wall-clock win, not just an inference trick.

## When to Use
- Long-context FT where sparse inference kernels do not accelerate training.

## When NOT to Use
Default on `task:posttrain-attention-sparsification` remains `method:sas`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:sas`.

## Gotchas & Failure Modes
- Not a replacement for `method:sas`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
