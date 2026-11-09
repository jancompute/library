---
id: method:sifr
type: method
title: 'SIFR (Stable Signed Flow Reinforcement)'
category: diffusion-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'on-policy self-distillation of a diffusion policy with bounded clean-output targets'
  reason: 'DiffusionOPSD remains image-policy OPSD; SIFR is signed-advantage flow RL with a drift budget'
  use_instead: method:diffusion-opsd
- when: 'teacher-free flow matching multi-objective alignment (Self-OPD)'
  reason: 'Self-OPD remains teacher-free velocity distill; SIFR is signed flow RL'
  use_instead: method:self-opd
- when: 'flow-model RL via proximal velocity matching (~100 updates vs Flow-GRPO ~4k)'
  reason: 'MEND is proximal velocity matching; SIFR is signed advantages plus Lagrange drift'
  use_instead: method:mend
- when: 'aggregation-first reward tilting for diffusion RL'
  reason: 'DiffusionART is aggregation-first tilting; SIFR is signed flow RL'
  use_instead: method:diffusionart
assumptions:
- 'Flow / rectified-flow T2I reward FT. Paper: SD3.5-M 2.5B, FLUX.2 Klein 9B, Cosmos 3 Super T2I 64B; 12 backbone–reward pairs. No public code as of 2026-11-09. arXiv 2611.09175 above watermark 2611.08453.'
last_reviewed: '2026-11-09'
papers:
- paper:sifr
recipes:
- recipe:sifr
claims:
- benchmark: '12 backbone–reward pairs on SD3.5-M 2.5B / FLUX.2 Klein 9B / Cosmos 3 Super T2I 64B'
  metric: 'reward vs iterative FT / flow RL; long-run collapse'
  value: 'matches or beats evaluated methods on all 12 pairs; faster peak; continues improving where baselines stall or collapse'
  baseline: 'iterative reward FT / Flow-GRPO-family / other signed-loss regularizers'
  date: '2026-11-09'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.09175'
  notes: 'Does not retarget method:diffusion-opsd / method:self-opd. Existing flow RL methods are signed-loss plus a regularization choice.'
tags:
- diffusion
- flow
- post-training
- active
---

# SIFR (Stable Signed Flow Reinforcement)

## Method Overview
SIFR replaces positive reward weights in iterative flow FT with signed advantages (an explicit unfitting term) and constrains velocity drift from a frozen reference with a Lagrange multiplier that tracks a prescribed drift budget.

## When to Use
- Multi-round reward FT of a flow T2I model when reweighting concentrates the distribution and the run collapses.

## When NOT to Use
Image-policy OPSD remains `method:diffusion-opsd`. Teacher-free flow matching remains `method:self-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:posttrain-diffusion`. Does **not** replace DiffusionOPSD / Self-OPD.

## Gotchas & Failure Modes
- No public code; recipe is a sketch of signed advantages plus the drift dual.
- Drift budget is a prescribed hyperparameter; too tight stalls reward, too loose reintroduces collapse.
