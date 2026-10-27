---
id: method:lstm-looped-kv
type: method
title: 'LSTM-Style Shared-KV Loop'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:recurrent-encoder-decoder-lm'
  reason: 'RLT remains experimental CED; this card shares one KV cache across an LSTM-style loop'
  use_instead: method:recurrent-looped-transformer
- when: 'Huginn-style dense fixed-point looped LMs'
  reason: 'Looped Models Done Right is the Huginn recipe; this card is shared-KV LSTM-style looping'
  use_instead: method:looped-models-done-right
assumptions:
- 'Shared-KV looped transformer. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:lstm-looped-kv
recipes:
- recipe:lstm-looped-kv
claims:
- benchmark: 'FineWeb looped transformer vs untied control / full-cache eval'
  metric: 'params; persistent cache sets; continuation-loss gap'
  value: 'width 1024: 40.4% fewer params; cache sets 15 to 4; last-10% consistency loss removes 81-89% of the continuation penalty'
  baseline: 'untied transformer; full-cache looped eval'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.33360'
  notes: 'Does not retarget method:recurrent-looped-transformer.'
tags:
- looped-lm
- active
---

# LSTM-Style Shared-KV Loop

## Method Overview
An LSTM-style looped transformer reuses one KV cache across recurrent steps and trains a late consistency loss so parallel teacher-forced caches match recursive continuation caches.

## When to Use
- Looped LMs that must cut persistent KV sets without a full CED redesign.

## When NOT to Use
Default on `task:recurrent-encoder-decoder-lm` remains `method:recurrent-looped-transformer`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:recurrent-looped-transformer`.

## Gotchas & Failure Modes
- Not a replacement for `method:recurrent-looped-transformer`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
