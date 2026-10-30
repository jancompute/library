---
id: method:air-elr
type: method
title: 'AIR (Affine Inverse-square-Root ELR)'
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:llm-pretraining-optimization'
  reason: 'Muon2 remains the ~7B dense pretrain optimizer; AIR is an ELR schedule under weight-normalized training'
  use_instead: method:muon2
assumptions:
- 'Weight-normalized / WN-style pretrain. 128B-token MoE. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:air-elr
recipes:
- recipe:air-elr
claims:
- benchmark: '128B-token MoE pretrain vs cosine at matched peak/terminal LR'
  metric: 'validation loss'
  value: '~0.01 lower loss vs cosine; WN vs WD collapse when ELR is matched'
  baseline: 'cosine LR; weight-decay vs weight-normalized at matched ELR'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.40362'
  notes: 'Does not retarget method:muon2.'
tags:
- optimizer
- lr-schedule
- active
---

# AIR (Affine Inverse-square-Root ELR)

## Method Overview
AIR schedules the effective learning rate under weight-normalized training: theoretically 1/sqrt(t) decay, then an affine remap so a finite run still hits a prescribed peak and terminal LR. Late-horizon ELR is the main gain; matching ELR makes WN and WD look alike.

## When to Use
- Weight-normalized or Muon-family pretrain where the nominal LR schedule is not the ELR the optimizer actually sees.

## When NOT to Use
Default on `task:llm-pretraining-optimization` remains `method:muon2`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:muon2`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- No public code as of 2026-10-30.
- Not a Muon2 bake-off; ELR matching is the claim, not a new optimizer.
