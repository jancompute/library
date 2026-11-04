---
id: method:dory
type: method
title: 'Dory'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the first hop on task:elastic-depth-looped-lm'
  reason: 'ELR remains mixed-depth elastic recurrence; Dory is an nGPT looped 4B recipe'
  use_instead: method:elr
assumptions:
- 'nGPT looped 4B, 6T tokens, 4.5T NVFP4. Official train code none; weights on Hugging Face. Mention on task:fp4-hardware-training.'
last_reviewed: '2026-11-04'
papers:
- paper:dory
recipes:
- recipe:dory
claims:
- benchmark: 'Dory1.0-4B 12-bench avg'
  metric: 'score at k=1 / 2 / 4 loops'
  value: '35.2 / 39.7 / 40.6 after 6T tokens (4.5T NVFP4)'
  baseline: 'same model at 1 loop'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03998'
  notes: 'Does not retarget method:elr or method:quartet-ii. Weights nvidia/nemotron-labs-dory.'
tags:
- architecture
- looped-lm
- nvfp4
- active
---

# Dory

## Method Overview
Dory trains an nGPT looped 4B with a difficulty-aware loop curriculum and last-loop KV, mostly in NVFP4.

## When to Use
- Elastic / mixed-depth looped pretrain when you want an nGPT 4B recipe with NVFP4 tokens and released weights.

## When NOT to Use
ELR remains the mixed-depth first hop. Quartet-II remains native FP4 hardware training. Looped Models Done Right remains Huginn-style.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:elr`.

## Gotchas & Failure Modes
- Official train code none; unofficial ports exist.
- Not a Quartet-II bake-off.
