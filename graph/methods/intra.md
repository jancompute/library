---
id: method:intra
type: method
title: 'INTRA'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:posttrain-attention-sparsification'
  reason: 'SAS remains gated post-train first hop; INTRA is static interleaved scatter/gather sparsity'
  use_instead: method:sas
assumptions:
- 'Static sparse attention. Code NovTi/INTRA.'
last_reviewed: '2026-10-27'
papers:
- paper:intra
recipes:
- recipe:intra
claims:
- benchmark: 'Hardware-aware static sparse attention vs local/strided patterns'
  metric: 'quality under CQS-compatible sparsity'
  value: 'scatter/gather relays keep global reachability without dense all-pairs coverage in each layer'
  baseline: 'local/strided sparse attention; SAS gated Top-K'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.34056'
  notes: 'Does not retarget method:sas.'
tags:
- sparse-attention
- active
---

# INTRA

## Method Overview
INTRA splits sparse layers into Scatter groups that sample neighborhoods and Gather groups that reconnect them, so long-range communication happens across layers instead of inside one dense softmax.

## When to Use
- Static sparse attention that must map to GPU query sets and still reach distant tokens.

## When NOT to Use
Default on `task:posttrain-attention-sparsification` remains `method:sas`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:sas`.

## Gotchas & Failure Modes
- Not a replacement for `method:sas`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
