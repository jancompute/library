---
id: method:hisa-rope
type: method
title: Hidden Sparse Attention
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'post-train gated sparse attention under a fixed budget'
    reason: 'SAS remains the post-train gated-budget hop; HiSA is from-scratch sparse QK (plus a conversion path)'
    use_instead: method:sas
  - when: 'on-policy discrete hybrid layer selection (FlashMorph2; not SAS gated budget)'
    reason: 'FlashMorph2 selects hybrid layers; HiSA sparsifies QK inside attention'
    use_instead: method:flashmorph2
  - when: 'choosing the ~7B dense pretrain optimizer'
    reason: 'Muon2 remains the optimizer; HiSA is an attention pattern'
    use_instead: method:muon2
  - when: 'genuine 1-bit PTQ (AF1 HiSA; not sparse QK)'
    reason: 'AF1 occupies the HiSA acronym for 1-bit PTQ; this card is Hidden Sparse Attention'
    use_instead: method:af1
assumptions:
  - '135M/360M from-scratch plus dense conversion. Slug is hisa-rope because method:af1 already uses HiSA. Code ambroise-b/hisa as of 2026-11-20. Concurrent ATFlash/WavePrune not ingested.'
last_reviewed: '2026-11-20'
papers:
- paper:hisa-rope
recipes:
- recipe:hisa-rope
claims:
- benchmark: '135M / 360M 4K val loss vs dense'
  metric: 'val loss / QK density'
  value: '135M 2.880 vs 2.906 at 29.3% QK; 360M 2.575 vs 2.587; 16K PG19 3.170 vs 3.205 at 20.2% QK'
  baseline: 'dense attention'
  date: '2026-11-20'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.26363'
  notes: 'Does not retarget method:sas / method:muon2. Distinct from method:af1 (1-bit PTQ HiSA).'
- benchmark: 'Flash-HiSA vs FA3'
  metric: 'val loss / tok/s / ρ'
  value: '2.892 vs 2.904; 238k vs 236k tok/s; ρ=34.8%'
  baseline: 'FlashAttention-3'
  date: '2026-11-20'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.26363'
  notes: 'Throughput match at lower QK density. Not a 7B bake-off.'
tags:
- sparse-attention
- pretrain
- hisa
- active
---

# Hidden Sparse Attention

## Method Overview
HiSA sparsifies QK while keeping RoPE. Train from scratch, or convert a dense checkpoint. The library slug is `hisa-rope` because `method:af1` already uses HiSA for 1-bit PTQ.

## When to Use
- From-scratch sparse attention when you want ~20–35% QK and FA3-like throughput.

## When NOT to Use
Post-train gated budget remains `method:sas`. Hybrid layer selection remains `method:flashmorph2`. 1-bit PTQ remains `method:af1`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:pretrain-dense-7b`. Mention on `task:posttrain-attention-sparsification`. Does **not** replace SAS or Muon2.

## Gotchas & Failure Modes
- Results are 135M/360M, not 7B.
- Concurrent ATFlash / WavePrune are not library nodes.
- Do not search the graph for `hisa` expecting this card; that slug is AF1.
