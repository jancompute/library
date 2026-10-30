---
id: method:idm
type: method
title: 'IDM'
category: diffusion-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'aligning text-to-image diffusion or flow models with rewards'
  reason: 'DiffusionOPSD / Self-OPD remain reward alignment; IDM is DMD + EMA moment matching'
  use_instead: method:diffusion-opsd
assumptions:
- 'DMD-style few-step generator with EMA. Official code inclusionAI/IDM.'
last_reviewed: '2026-10-30'
papers:
- paper:idm
recipes:
- recipe:idm
claims:
- benchmark: 'LongText-Bench ZH/EN at two network evaluations (Z-Image-Turbo 6B / Qwen-Image 20B)'
  metric: 'LongText-Bench'
  value: '94.25% Chinese / 90.20% English, highest among compared methods at 2 NFE'
  baseline: 'DMD without explicit moment constraint'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.39633'
  notes: 'Does not retarget method:diffusion-opsd.'
tags:
- diffusion
- distillation
- active
---

# IDM

## Method Overview
IDM is distribution-matching distillation that keeps DMD's score difference and also matches feature means and per-coordinate standard deviations using the generator EMA as the reference. No extra fake-score net and no external encoder.

## When to Use
- One-step or few-step T2I distillation where DMD already runs and an explicit moment constraint is cheap.

## When NOT to Use
Reward alignment first hop remains DiffusionOPSD / Self-OPD.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:diffusion-opsd` or `method:self-opd`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Few-step T2I distillation, not image-policy RL.
