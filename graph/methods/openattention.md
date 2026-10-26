---
id: method:openattention
type: method
title: 'OpenAttention'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:posttrain-attention-sparsification'
  reason: 'SAS remains the gated post-train first hop; OpenAttention keeps a 1-token proxy for the unread tail'
  use_instead: method:sas
assumptions:
- 'Sparse attention at very low read fractions. Code hyunwoo137/OpenAttention.'
last_reviewed: '2026-10-26'
papers:
- paper:openattention
recipes:
- recipe:openattention
claims:
- benchmark: 'Sparse attention at ~1% KV reads vs discarding or sampling the unread tail'
  metric: 'quality at 1-5% KV reads'
  value: 'one token that folds the unread tail beats discard/sample at 5% reads and below'
  baseline: 'tail discard; tail sampling; SAS gated Top-K'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.30951'
  notes: 'Does not retarget method:sas.'
tags:
- sparse-attention
- active
---

# OpenAttention

## Method Overview
OpenAttention folds the unread KV tail into one proxy token so 1% reads stay usable when sampling the tail misses heavy hitters.

## When to Use
- Post-train sparse attention at 1-5% reads where dropping the tail biases the output.

## When NOT to Use
Default on `task:posttrain-attention-sparsification` remains `method:sas`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:sas`.

## Gotchas & Failure Modes
- Not a replacement for `method:sas`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
