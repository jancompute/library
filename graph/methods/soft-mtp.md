---
id: method:soft-mtp
type: method
title: 'Soft-MTP'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'lossless multi-token / diffusion-augmented AR serving'
  reason: 'Uno remains the serving first hop; Soft-MTP is an MTP pretrain gradient fix'
  use_instead: method:uno
- when: 'causal self-recursion MTP without auxiliary heads (ECHO)'
  reason: 'ECHO is backbone MTP self-recursion; Soft-MTP is a CE residual fix on auxiliary MTP heads'
  use_instead: method:echo-mtp
assumptions:
- 'Shared linear output head between NTP and MTP. Official code JaydenTeoh/Soft-MTP.'
last_reviewed: '2026-10-30'
papers:
- paper:soft-mtp
recipes:
- recipe:soft-mtp
claims:
- benchmark: 'MTP pretrain: KL self-distillation vs standard MTP CE residual'
  metric: 'MTP gradient SNR / speculative-decode acceptance'
  value: 'KL term recovered without vocab-sized logits; residual dropped'
  baseline: 'standard MTP cross-entropy'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.38331'
  notes: 'Does not retarget method:uno.'
tags:
- mtp
- distillation
- active
---

# Soft-MTP

## Method Overview
Soft-MTP is a one-line change to multi-token prediction: route the NTP and MTP cross-entropy gradients so the update is the KL that pulls each MTP head toward the model's own next-token distribution, and drop the residual that otherwise fights both NTP and MTP as width grows.

## When to Use
- Pretraining or continued-pretrain MTP heads used for speculative decoding.

## When NOT to Use
Lossless diffusion-augmented AR serving first hop remains `method:uno`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:uno` or `method:echo-mtp`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Pretrain MTP objective, not a serving kernel.
