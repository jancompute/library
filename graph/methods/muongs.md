---
id: method:muongs
type: method
title: 'MuonGS'
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:llm-pretraining-optimization'
  reason: 'Muon2 remains the ~7B dense pretrain optimizer; MuonGS is Gram-Schmidt radial projection vs MuonH at 160M/400M/1B-MoE'
  use_instead: method:muon2
- when: 'Hyperbolic MuonH wrapper on consumer ~2B pretrain'
  reason: 'Puro-2B documents MuonH; MuonGS is a radial-projection alternative at small scale'
  use_instead: method:puro-2b
assumptions:
- 'Dense 160M/400M and 135M-active/1B-total MoE vs MuonH. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:muongs
recipes:
- recipe:muongs
claims:
- benchmark: '160M/400M dense and 135M-active 1B-total MoE pretrain vs MuonH'
  metric: 'validation perplexity; token-equivalent speedup at matched val loss'
  value: 'lower val PPL than MuonH at long horizon; dense token-equivalent speedup up to about 15% vs MuonH'
  baseline: 'MuonH; MuonW; vanilla Muon'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37647'
  notes: 'Does not retarget method:muon2.'
tags:
- optimizer
- muon
- active
---

# MuonGS

## Method Overview
MuonGS strips the radial component of each Muon update with Gram-Schmidt projection without freezing the weight norm, so accumulated effective learning rate grows like sqrt(T) instead of logarithmically.

## When to Use
- Muon-family pretrain where vanilla Muon stalls because weight-norm growth starves effective step size, and you would otherwise switch to MuonH.

## When NOT to Use
Default on `task:llm-pretraining-optimization` remains `method:muon2`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:muon2`.

## Gotchas & Failure Modes
- Not a replacement for `method:muon2`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
