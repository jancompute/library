---
id: method:tuon
type: method
title: 'TUON'
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:llm-pretraining-optimization'
  reason: 'Muon2 remains the ~7B optimizer default; TUON mixes layers then polarizes T-SVD slices'
  use_instead: method:muon2
- when: 't-SVD grouping of Muon updates (T-MUON)'
  reason: 'T-MUON groups Muon updates; TUON mix-then-polarizes across layers'
  use_instead: method:t-muon
assumptions:
- 'Tensor-aware Muon-family pretrain optimizer. Distinct from method:t-muon. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:tuon
recipes:
- recipe:tuon
claims:
- benchmark: 'LLM pretrain optimizer vs per-layer Muon / unfolding tensor methods'
  metric: 'cross-layer polar updates under T-SVD mix'
  value: 'mix-then-polarize captures cross-layer correlation without globally unfolding; not QKV-only'
  baseline: 'Muon2 per-layer polar; T-MUON; unfolding tensor polar'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.35130'
  notes: 'Does not retarget method:muon2. Distinct from method:t-muon.'
tags:
- optimizer
- active
---

# TUON

## Method Overview
TUON applies a unitary mix across layers, polarizes each transformed slice, and inverts the mix so the update sees cross-layer structure without flattening everything into one matrix.

## When to Use
- Pretrain where per-layer Muon ignores correlated layers and unfolding tensor methods stay shallow.

## When NOT to Use
Default on `task:llm-pretraining-optimization` remains `method:muon2`. Not `method:t-muon`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:muon2`. Distinct from `method:t-muon`.

## Gotchas & Failure Modes
- Not a replacement for `method:muon2`.
- Distinct from `method:t-muon`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
