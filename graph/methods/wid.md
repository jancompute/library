---
id: method:wid
type: method
title: 'WiD'
category: diffusion
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'pixel-space DiT / flow-matching image pretrain (Representation Guidance)'
  reason: 'RG remains pixel DiT first hop; WiD is a native-decoder plug-in on PixelDiT/DeCo, not a head-to-head vs RG'
  use_instead: method:representation-guidance
- when: 'aligning text-to-image diffusion or flow models with rewards'
  reason: 'WiD is pixel-decoder pretrain; DiffusionOPSD / Self-OPD remain reward alignment'
  use_instead: method:diffusion-opsd
- when: 'Schedule-Free / LR decay instead of constant-LR EMA for large diffusion'
  reason: 'WiD is the decoder path; Schedule-Free is the optimizer/EMA schedule'
  use_instead: method:schedule-free-diffusion
assumptions:
- 'Pixel-space flow / PixelDiT or DeCo decoder. ImageNet class-conditional and DeCo T2I. Code promised after acceptance; none public as of 2026-10-29.'
last_reviewed: '2026-10-29'
papers:
- paper:wid
recipes:
- recipe:wid
claims:
- benchmark: 'ImageNet-256 PixelDiT-XL/16 FID; ImageNet-512 FID; DeCo-XXL GenEval / DPG-Bench'
  metric: 'FID / GenEval / DPG-Bench'
  value: 'IN-256 FID 1.53 at 500 epochs vs native PixelDiT 1.54 at 800; IN-512 FID 1.64 after 260+50 vs native 1.81 at 320+530; GenEval 0.49 vs 0.43; DPG 78.8 vs 73.1'
  baseline: 'native PixelDiT-XL / DeCo-XXL (single-paper)'
  date: '2026-10-29'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36192'
  notes: 'Not a head-to-head vs Representation Guidance (IN-256 FID 1.55, different architecture). Does not retarget method:representation-guidance.'
tags:
- diffusion
- pixel-dit
- active
---

# WiD

## Method Overview
WiD injects a trainable patch-PCA Wiener path into a native pixel decoder: analysis coefficients get a noise-level Wiener gain, enter the decoder as extra features, and the decoder predicts a coefficient correction that is added to the residual pixel velocity under the original flow objective.

## When to Use
- Pixel-space PixelDiT / DeCo training where native velocity learning is slow and a statistical decoder prior is acceptable.

## When NOT to Use
Pixel DiT architecture first hop → `method:representation-guidance`. Reward alignment → `method:diffusion-opsd`. Optimizer/EMA schedule → `method:schedule-free-diffusion`.

## Relation to Existing SOTA
Active plug-in on `task:pixel-diffusion-pretrain` (`sota_for: []`). Does **not** replace Representation Guidance.

## Gotchas & Failure Modes
- No public code as of 2026-10-29.
- Not an ImageNet FID bake-off against Representation Guidance.
- ~1% extra parameters (797M → 805M on PixelDiT-XL); statistics from ~4% of ImageNet.
