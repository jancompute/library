---
id: method:musam
type: method
title: 'Sharpness-Aware Muon (MuSAM / MoMuSAM)'
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:llm-pretraining-optimization'
  reason: 'Muon2 remains the ~7B dense pretrain optimizer; MuSAM/MoMuSAM add SAM-style neighborhood perturbations on Muon'
  use_instead: method:muon2
- when: 'Muon spectral clip of momentum singular values (Musec)'
  reason: 'Musec clips singular values; MuSAM perturbs along Muon/momentum directions'
  use_instead: method:musec
assumptions:
- 'Standard vision/LM sharpness-aware ablations on Muon. Extra gradient for MuSAM; MoMuSAM reuses momentum. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:musam
recipes:
- recipe:musam
claims:
- benchmark: 'Standard sharpness-aware optimizer benchmarks vs Muon'
  metric: 'generalization / neighborhood worst-case loss'
  value: 'sharpness awareness consistently improves Muon; MoMuSAM matches MuSAM stationarity order without the extra clean gradient'
  baseline: 'Muon; SAM'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37225'
  notes: 'Does not retarget method:muon2.'
tags:
- optimizer
- muon
- sam
- active
---

# Sharpness-Aware Muon (MuSAM / MoMuSAM)

## Method Overview
MuSAM applies a SAM-style perturbation on Muon's orthogonalized update. MoMuSAM uses normalized Muon momentum as the perturbation direction so the extra clean-gradient step is dropped and the proxy is temporally aggregated.

## When to Use
- Muon training where neighborhood worst-case loss / flat minima are the goal and a SAM-style second gradient is acceptable, or MoMuSAM when that extra gradient is not.

## When NOT to Use
Default on `task:llm-pretraining-optimization` remains `method:muon2`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:muon2`.

## Gotchas & Failure Modes
- Not a replacement for `method:muon2`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
