---
id: method:specopd
type: method
title: 'SpecOPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'lossless multi-token / diffusion-augmented AR serving'
  reason: 'Uno remains serving; SpecOPD is branch-parallel OPD for speculative drafters'
  use_instead: method:uno
- when: 'same-tokenizer single-teacher matching distillation'
  reason: 'OPD remains matching; SpecOPD trains SD drafters, not a general student'
  use_instead: method:opd
assumptions:
- 'Parallel drafters (DFlash / DSpark / DFlash V2) on 8B / 27B / 125B targets. Distinct from MDraft (diffusion drafters). HF Daily leftover below watermark. No SpecOPD repo; Draft-OPD is related prior art.'
last_reviewed: '2026-11-05'
papers:
- paper:specopd
recipes:
- recipe:specopd
claims:
- benchmark: 'DFlash / DSpark / DFlash V2 on 8B GQA, 27B GQA–GDN, 125B QSA–GDN'
  metric: 'mean acceptance length; supervised-token throughput; generation speedup'
  value: 'up to +41.45% mean AL; 16.09× supervised-token throughput vs sequential OPD; 3.56× vs AR'
  baseline: 'sequential draft-and-verify OPD / AR decode'
  date: '2026-11-05'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.02846'
  notes: 'E2E-TV surrogate on packed proposal trees. Does not retarget method:uno or method:opd. Distinct from method:mdraft.'
tags:
- speculative-decoding
- opd
- drafter
- active
---

# SpecOPD

## Method Overview
SpecOPD trains speculative drafters with branch-parallel on-policy distillation. A draft block is supervised from its reference prefix and sampled history, not from a sequential draft-and-verify rollout. Branches pack into proposal trees that share target-prefix compute (tree masks for GQA, indexer groups for QSA, indexed state replay for GDN). The drafter is trained with an E2E-TV surrogate on acceptance length.

## When to Use
- Pushing a well-trained parallel drafter (DFlash / DSpark / DFlash V2) past an acceptance-length plateau without serializing draft-and-verify collection.

## When NOT to Use
Uno remains the diffusion-augmented AR serving hop. OPD remains general student matching. MDraft is multi-draft OPD for diffusion drafters, not this SD executor.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:diffusion-augmented-ar` with a mention on `task:student-distillation`. Does **not** replace `method:uno`, `method:opd`, or `method:mdraft`.

## Gotchas & Failure Modes
- On-policy here is drafter-sampled branches at reference anchors, not live verified responses.
- No dedicated SpecOPD GitHub as of 2026-11-05.
