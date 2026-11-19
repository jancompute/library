---
id: method:curvdelta
type: method
title: CurvDelta
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'single-adapter quality LoRA / rsLoRA + LR sweep rather than stacking adapters'
    reason: 'Quality default remains vanilla LoRA + rsLoRA + LR sweep; CurvDelta is K-FAC low-curvature sequential PEFT'
    use_instead: method:lr-matters-lora
  - when: 'stacking independently trained LoRA adapters / sequential skill add without an inference router'
    reason: 'READ remains LoRA skill composition; CurvDelta is curvature-constrained sequential FT'
    use_instead: method:read-lora
  - when: 'multi-stage agent capability stacking / continual learning'
    reason: 'ACLArena remains agent CL; CurvDelta is PEFT geometry, not agent LoRA experts'
    use_instead: method:aclarena
assumptions:
  - 'K-FAC curvature of the current task. Constrain the update to a low-curvature subspace. Paper: Gemma-3-1B / Llama-2-7B sequential math+code; Llama-3.1-8B TOFU. Code xiaozi-max/curvdelta_learning as of 2026-11-19. Does not supersede lr-matters-lora.'
last_reviewed: '2026-11-19'
papers:
- paper:curvdelta
recipes:
- recipe:curvdelta
claims:
- benchmark: 'Gemma-3-1B sequential math ALL vs FT / LoRA'
  metric: 'ALL accuracy'
  value: '22.2 vs FT 19.4 / LoRA 17.5'
  baseline: 'FT / LoRA'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.24654'
  notes: 'Does not supersede method:lr-matters-lora. Code xiaozi-max/curvdelta_learning.'
- benchmark: 'Llama-2-7B sequential math / code ALL vs Replay / FT / LoRA'
  metric: 'ALL accuracy'
  value: 'math CurvLoRA 40.1 vs Replay 40.2 / FT 33.4; code 42.8 vs LoRA 41.7 / FT 39.6'
  baseline: 'Replay / FT / LoRA'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.24654'
  notes: 'Does not supersede lr-matters-lora. TOFU SimNPO Llama-3.1-8B CurvLoRA Forget 10% FP 3.4 / MU 62.5 vs Retrain 10.6 / 64.6.'
tags:
- peft
- lora
- kfac
- curvature
- continual
- active
---

# CurvDelta

## Method Overview
CurvDelta and CurvLoRA constrain PEFT updates to a K-FAC low-curvature subspace so sequential tasks overwrite less of prior skills.

## When to Use
- Sequential PEFT / unlearning when vanilla LoRA overwrites earlier tasks.

## When NOT to Use
24GB quality LoRA remains `method:lr-matters-lora`. LoRA skill composition remains `method:read-lora`. Agent continual learning remains `method:aclarena`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:lora-quality-tuning`. Mention on `task:parameter-efficient-fine-tuning`. Does **not** supersede vanilla LoRA + rsLoRA + LR sweep.

## Gotchas & Failure Modes
- K-FAC estimate cost sits on top of LoRA.
- Unlearning code is a second repo (curvdelta_unlearning).
