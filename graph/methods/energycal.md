---
id: method:energycal
type: method
title: 'EnergyCal'
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'Muon raises first MoE layer routing-bias span'
    reason: 'EnergyCal damps routed-expert Newton-Schulz energy; this gotcha is first-layer bias span'
    use_instead: paper:muon-first-moe-layer
  - when: 'the locked first hop on task:llm-pretraining-optimization'
    reason: 'Muon2 remains the ~7B dense pretrain optimizer; EnergyCal attenuates routed-expert Muon updates on sparse MoE spikes'
    use_instead: method:muon2
  - when: 'choosing the frontier MoE architecture template'
    reason: 'DeepSeek-V4 / Kimi-K3 remain the MoE template; EnergyCal is a Muon spike damper'
    use_instead: task:pretrain-moe-frontier
assumptions:
- '4B-parameter sparse MoE with MuonH / Muon. No persistent optimizer state. No public code as of 2026-10-28.'
last_reviewed: '2026-10-30'
papers:
  - paper:muon-first-moe-layer
  - paper:energycal
recipes:
- recipe:energycal
claims:
- benchmark: '4B sparse MoE Muon-family training vs lower-LR MuonH'
  metric: 'mean thresholded loss-spike burden; geometric-mean perplexity'
  value: 'EnergyCal-MuonH cuts mean spike burden 99.51% and final geomean PPL 4.06% vs a lower-LR MuonH recipe; plain Muon spike burden -95.98% across two exponents'
  baseline: 'development-selected lower-LR MuonH; plain Muon at matched LR/WD'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37062'
  notes: 'Does not retarget method:muon2.'
tags:
- optimizer
- muon
- moe
- active
---

# EnergyCal

## Method Overview
EnergyCal attenuates routed-expert updates by the normalized squared Frobenius norm of their finite-step Newton-Schulz directions. It leaves the spectral transform unchanged and adds no persistent optimizer state.

## When to Use
- Sparse MoE pretrain with Muon-family optimizers that produce large loss spikes on routed experts.

## When NOT to Use
Default on `task:llm-pretraining-optimization` remains `method:muon2`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:muon2`.

## Gotchas & Failure Modes
- Not a replacement for `method:muon2`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
