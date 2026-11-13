---
id: method:foam
type: method
title: FOAM
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the ~7B dense pretrain optimizer'
    reason: 'Muon2 remains the 7B default; FOAM is a SOAP-memory plug-in that matches SOAP quality at AdamW-like wall-clock'
    use_instead: method:muon2
  - when: 'high-memory full SOAP / KL-SOAP at unconstrained batch'
    reason: 'KL-SOAP remains the large-batch second-order hop; FOAM drops the output-side SOAP factor'
    use_instead: method:soap-muon-scale
  - when: 'Nyström-sketched SOAP / linear optimizer-state memory (Clean / Q-Clean)'
    reason: 'Clean sketches the SOAP preconditioner; FOAM is input-only SOAP plus factored Adam moment'
    use_instead: method:clean
assumptions:
  - 'Dense transformer pretrain where SOAP quality is wanted but SOAP optimizer state and eigendecomposition are too expensive. Paper: 124M–760M. GitHub naver-ai/foam is README-only as of 2026-11-13.'
last_reviewed: '2026-11-13'
papers:
- paper:foam
recipes:
- recipe:foam
claims:
- benchmark: '124M–760M dense pretrain val loss / wall-clock / optimizer state'
  metric: 'val loss vs Muon and SOAP; t_A vs AdamW; SOAP-state fraction; peak mem vs AdamW'
  value: 'matches Muon/SOAP val loss 124M–760M; t_A within 7% of AdamW; 51% of SOAP wall-clock to SOAP quality; ~50% SOAP optimizer state; peak mem +7.4% vs AdamW (SOAP +12.9%)'
  baseline: 'Muon / SOAP / AdamW'
  date: '2026-11-13'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.16905'
  notes: 'Does not retarget method:muon2 or method:soap-muon-scale. Distinct from method:clean. Mention on task:full-param-memory-efficient-pretrain. Hugging Face Daily leftover (not on the 2026-11-13 cs.LG/CL/AI listing).'
tags:
- optimizer
- soap
- pretraining
- active
---

# FOAM

## Method Overview
FOAM (Factored One-sided Adam-Moment) is a SOAP variant that preconditions only the input Gram and stores Adam's second moment in the same Kronecker factors. The output-side SOAP eigendecomposition is dropped. The result tracks SOAP and Muon validation loss from 124M to 760M at about half of SOAP's optimizer state and AdamW-like wall-clock.

## When to Use
- SOAP-quality dense pretrain when SOAP memory and eigendecomposition dominate, and a Muon2 or KL-SOAP run is not already locked.

## When NOT to Use
The ~7B optimizer default remains `method:muon2`. Unconstrained-memory large-batch SOAP remains `method:soap-muon-scale`. Nyström SOAP sketches remain `method:clean`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:llm-pretraining-optimization`. Mention on `task:full-param-memory-efficient-pretrain`. Does **not** replace Muon2, KL-SOAP, or Clean.

## Gotchas & Failure Modes
- GitHub `naver-ai/foam` is README-only as of 2026-11-13 (`code_status: announced`).
- Paper scale is 124M–760M; do not treat the 7B default as retargeted.
- Input-only SOAP can miss output-side curvature that full SOAP / KL-SOAP keep.
