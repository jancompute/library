---
id: method:lambdamix
type: method
title: 'LambdaMix'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'Pearson-normalize multi-reward GRPO covariances (large correlated rewards suppress smaller ones)'
  reason: 'LambdaMix is a preference-conditioned LoRA family; CorrGRPO is scalarized multi-reward aggregation'
  use_instead: method:corrgrpo
- when: 'density-aware multi-reward aggregation (inverse-sqrt active-group density)'
  reason: 'DARA reweights GDPO-style advantages; LambdaMix mixes adapters and preference weights'
  use_instead: method:dara
- when: 'the locked 24GB LoRA quality default'
  reason: 'Quality default remains vanilla LoRA + rsLoRA + LR sweep; LambdaMix is multi-objective GRPO adapters'
  use_instead: method:lr-matters-lora
- when: 'single-turn dense math/code Pass@1 RLVR (one verifier reward)'
  reason: 'CISPO remains Pass@1; LambdaMix is a two-objective preference family'
  use_instead: method:cispo
assumptions:
- 'One LoRA per objective on a frozen base. Preference vector mixes adapters at generate and weights separately normalized rewards. Paper: four models; 500 GRPO updates; 32k completions vs specialist GRPO 5 runs / 160k. Code ckarouzos/lambdamix released as of 2026-11-09. arXiv 2611.09634 above watermark 2611.08453.'
last_reviewed: '2026-11-09'
papers:
- paper:lambdamix
recipes:
- recipe:lambdamix
claims:
- benchmark: 'Qwen3.5-9B PKU-SafeRLHF / GSM8K-IF hypervolume (Table 1 / Figure 3)'
  metric: 'HV vs strongest conditioned or GRPO baseline'
  value: 'PKU-SafeRLHF 0.8735 vs prompt conditioning 0.7760; GSM8K-IF 0.8099 vs GRPO 0.6947'
  baseline: 'prompt conditioning / GRPO / GDPO / HoE / policy merging'
  date: '2026-11-09'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.09634'
  notes: 'Does not retarget method:corrgrpo / method:dara. Joint adapter mix + objective weights; GDPO-style per-objective standardization helps HH, mixed on GSM8K-IF.'
tags:
- post-training
- peft
- multi-reward
- active
---

# LambdaMix

## Method Overview
LambdaMix trains one LoRA per competing objective on a frozen base. At each step a preference vector $\lambda$ mixes the adapters that generate the group and weights the separately normalized rewards that update those adapters. Inference reuses the same mix without a second optimization run.

## When to Use
- Multi-objective GRPO where user preferences change at deploy time and a bank of specialist policies is too expensive.

## When NOT to Use
Scalarized multi-reward aggregation remains `method:corrgrpo` / `method:dara`. Single-adapter quality LoRA remains `method:lr-matters-lora`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:multi-reward-rlvr` with a mention on `task:parameter-efficient-fine-tuning`. Does **not** replace CorrGRPO / DARA.

## Gotchas & Failure Modes
- Jointly varying mix and weights is required; mixture-only or weight-only collapses the preference span.
- GDPO-style reward standardization helps helpfulness–harmlessness HV on all four models and can hurt GSM8K-IF / rewrite HV.
