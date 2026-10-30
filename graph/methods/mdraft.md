---
id: method:mdraft
type: method
title: 'MDraft'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'lossless multi-token / diffusion-augmented AR serving'
  reason: 'Uno remains serving; MDraft is drafter OPD under prefix mismatch'
  use_instead: method:uno
assumptions:
- 'Parallel diffusion drafter plus AR verifier. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:mdraft
recipes:
- recipe:mdraft
claims:
- benchmark: 'parallel diffusion drafter OPD vs per-prefix independent targets'
  metric: 'draft acceptance'
  value: 'aggregate verifier conditionals across sampled prefixes'
  baseline: 'independent on-policy distill per sampled prefix'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37778'
  notes: 'Does not retarget method:uno.'
tags:
- speculative-decoding
- opd
- active
---

# MDraft

## Method Overview
MDraft is OPD for parallel diffusion drafters. Sample several draft blocks from one prefix, let the AR verifier score each in-block position under its sampled prefix, and average those full-vocab conditionals so a token that is good after some prefixes is not zeroed out.

## When to Use
- Training a one-step / block diffusion drafter with on-policy verifier distillation.

## When NOT to Use
Uno remains the lossless diffusion-augmented AR serving first hop.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:uno` or `method:dstill`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- No public code as of 2026-10-30.
