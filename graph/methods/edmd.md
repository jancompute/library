---
id: method:edmd
type: method
title: eDMD
category: diffusion-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'aligning text-to-image diffusion or flow models with rewards'
    reason: 'DiffusionOPSD remains reward OPSD; eDMD is few-step endpoint-only fake-score DMD'
    use_instead: method:diffusion-opsd
  - when: 'intrinsic distribution matching / EMA moment constraint on DMD (IDM)'
    reason: 'IDM is DMD plus EMA moments; eDMD trains the fake model only on the student final outputs'
    use_instead: method:idm
  - when: 'few-step average-velocity diffusion RL (FewStepRL; not DiffusionOPSD default)'
    reason: 'FewStepRL ports RL hosts onto average-velocity few-step models; eDMD is endpoint DMD distillation'
    use_instead: method:fewsteprl
assumptions:
  - '4-step distillation of SD3-Medium, FLUX.2-klein 4B/9B, Qwen-Image-2.1. No real images. Code released at Westlake-AGI-Lab/eDMD as of 2026-11-16.'
last_reviewed: '2026-11-16'
papers:
- paper:edmd
recipes:
- recipe:edmd
claims:
- benchmark: '4-step students of SD3-Medium / FLUX.2-klein-4B / FLUX.2-klein-9B, DrawBench-1000 peak HPSv3++'
  metric: 'peak HPSv3++'
  value: 'SD3-M 11.171 vs D-DMD 10.841; FLUX.2-klein-4B 12.699 vs DMD2 11.337; FLUX.2-klein-9B 12.431 vs D-DMD 11.325'
  baseline: 'DMD2 / TDM / D-DMD / CDM'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.17194'
  notes: 'Does not retarget method:diffusion-opsd / method:self-opd. Distinct from method:idm / method:fewsteprl / method:dfr. HF leftover 2611.17194.'
- benchmark: 'Held-out HPSv3++ lead vs strongest baseline on SD3-M / FLUX.2-klein-4B / 9B / Qwen-Image'
  metric: 'HPSv3++ delta'
  value: '+0.30 / +1.37 / +1.11 / +0.47; Qwen-Image peak 14.69 vs backprop-only 13.60'
  baseline: 'strongest DMD-family baseline; backprop-only'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.17194'
  notes: 'No real images. Precise teacher is a short multi-step on the final noise interval plus calibrated query density.'
tags:
- diffusion
- dmd
- few-step
- active
---

# eDMD

## Method Overview
eDMD (Endpoint Distribution Matching) trains the fake score model only on the student's final outputs. A precise teacher (short multi-step on the final noise interval) plus calibrated query density replaces full-trajectory fake-score DMD. No real images.

## When to Use
- Few-step distillation of a large T2I / flow teacher when full-trajectory DMD is the current recipe.

## When NOT to Use
Reward OPSD remains `method:diffusion-opsd`. Teacher-free flow matching remains `method:self-opd`. EMA-moment DMD remains `method:idm`. Average-velocity few-step RL remains `method:fewsteprl`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:posttrain-diffusion`. Does **not** replace DiffusionOPSD or Self-OPD.

## Gotchas & Failure Modes
- Endpoint fake-score, not reward OPSD and not few-step RL.
- Code: `https://github.com/Westlake-AGI-Lab/eDMD` (`code_status: released`).
