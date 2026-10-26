---
id: method:lora-init-asymmetric
type: method
title: 'LoRA Init Asymmetric'
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:lora-quality-tuning'
  reason: 'Quality default remains vanilla LoRA + rsLoRA + LR sweep; this card re-inits LoRA so LoRA+ asymmetric LRs are less brittle'
  use_instead: method:lr-matters-lora
assumptions:
- 'LoRA+ style per-factor LRs. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:lora-init-asymmetric
recipes:
- recipe:lora-init-asymmetric
claims:
- benchmark: 'LoRA / LoRA+ LR sensitivity vs initialization that stabilizes asymmetric LRs'
  metric: 'robustness of LoRA+ asymmetric LRs to the LR grid'
  value: 'initialization that makes asymmetric A/B LRs less brittle vs vanilla LoRA init'
  baseline: 'vanilla LoRA init; LoRA+ asymmetric LRs without the init'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32142'
  notes: 'Does not retarget method:lr-matters-lora.'
tags:
- peft
- lora
- active
---

# LoRA Init Asymmetric

## Method Overview
Once LRs are tuned, vanilla LoRA stays competitive. This card re-initializes LoRA so LoRA+ asymmetric LRs are less grid-brittle.

## When to Use
- LoRA+ runs where A/B LR asymmetry is wanted but the LR grid is expensive.

## When NOT to Use
Default on `task:lora-quality-tuning` remains `method:lr-matters-lora`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:lr-matters-lora`.

## Gotchas & Failure Modes
- Not a replacement for `method:lr-matters-lora`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
