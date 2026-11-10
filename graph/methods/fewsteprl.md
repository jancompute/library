---
id: method:fewsteprl
type: method
title: 'FewStepRL'
category: rl-algorithm
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'aligning text-to-image diffusion or flow models with rewards'
  reason: 'DiffusionOPSD remains on-policy self-distill; FewStepRL ports hosts onto average-velocity few-step models'
  use_instead: method:diffusion-opsd
assumptions:
- 'A few-step average-velocity diffusion/flow checkpoint. Paper adapts FlowGRPO / AWM / DiffusionNFT / DiffusionOPSD / ReFL. No public code as of 2026-11-10. HF Daily leftover below watermark 2611.09634, ingested 2026-11-10. arXiv 2611.08240.'
last_reviewed: '2026-11-10'
papers:
- paper:fewsteprl
recipes:
- recipe:fewsteprl
claims:
- benchmark: 'few-step average-velocity diffusion RL hosts'
  metric: 'host adaptation vs FlowGRPO / AWM / DiffusionNFT / DiffusionOPSD / ReFL'
  value: 'ports those hosts onto average-velocity few-step models; not a DiffusionOPSD bake-off'
  baseline: 'FlowGRPO / AWM / DiffusionNFT / DiffusionOPSD / ReFL'
  date: '2026-11-10'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.08240'
  notes: 'Does not retarget method:diffusion-opsd or method:self-opd. HF leftover below watermark 2611.09634.'
tags:
- diffusion
- rl
- few-step
- average-velocity
- active
---

# FewStepRL

## Method Overview
FewStepRL keeps existing diffusion-RL hosts and changes the sampler to a few-step average-velocity parameterization.

## When to Use
- Reward alignment of an already few-step average-velocity diffusion/flow model.

## When NOT to Use
Image/flow reward default remains `method:diffusion-opsd` + `method:self-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:posttrain-diffusion`. Does **not** replace DiffusionOPSD or Self-OPD.

## Gotchas & Failure Modes
- No public trainer.
- Below-watermark HF leftover; ingested because it changes the few-step host, not because it retargets SOTA.
- Not a pixel-DiT pretrain method.
