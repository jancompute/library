---
id: method:tdlm
type: method
title: 'TDLM'
category: diffusion
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:diffusion-lm-ar-delta-recycle'
  reason: 'A2D remains AR-delta recycle; TDLM adds temporal self-conditioning inside a frozen masked dLLM denoiser'
  use_instead: method:a2d
- when: 'continuous diffusion language model pretrain (SemiCat)'
  reason: 'SemiCat is continuous DLM pretrain; TDLM is discrete masked-dLLM temporal attention'
  use_instead: method:semicat
assumptions:
- 'LLaDA / Dream frozen denoisers plus ~0.84% temporal parameters. Self-generated trajectories. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:tdlm
recipes:
- recipe:tdlm
claims:
- benchmark: 'LLaDA and Dream masked dLLMs vs original diffusion LMs'
  metric: 'generation speed; quality vs original DLM'
  value: 'up to 7.15x faster generation than the original diffusion LM; temporal modules add about 0.84% trainable parameters on LLaDA'
  baseline: 'original LLaDA / Dream denoisers without temporal self-conditioning'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36940'
  notes: 'Does not retarget method:a2d.'
tags:
- diffusion
- dllm
- active
---

# TDLM

## Method Overview
TDLM lets each unresolved position attend to its own history of hidden states inside a frozen denoiser. Training uses self-generated trajectories and cross-entropy on tokens revealed between consecutive sampled steps.

## When to Use
- Masked dLLM serving/training where later denoise steps recompute representations that earlier steps already had.

## When NOT to Use
Default on `task:diffusion-lm-ar-delta-recycle` remains `method:a2d`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:a2d`.

## Gotchas & Failure Modes
- Not a replacement for `method:a2d`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
