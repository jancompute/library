---
id: method:remar
type: method
title: ReMaRL
category: diffusion
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'recycle an AR post-training weight delta onto a converted dLLM'
    reason: 'A2D remains AR-delta recycle; ReMaRL is a 0.3M GRPO unmask/retain/remask policy on a frozen dLLM'
    use_instead: method:a2d
  - when: 'temporal self-conditioning inside a frozen masked dLLM (TDLM)'
    reason: 'TDLM stores per-position hidden history in a frozen denoiser; ReMaRL learns a remask policy'
    use_instead: method:tdlm
  - when: 'dLLM RL that forks from high-entropy intermediate states (ForkGRPO)'
    reason: 'ForkGRPO updates the dLLM from entropy forks; ReMaRL keeps the dLLM frozen and trains a tiny position policy'
    use_instead: method:forkgrpo
  - when: 'continuous diffusion language model pretrain (self-conditioning / SemiCat)'
    reason: 'SemiCat is continuous pretrain; ReMaRL is discrete remasking at inference'
    use_instead: method:semicat
assumptions:
  - 'Frozen masked dLLM (LLaDA-8B-Instruct / Dream-v0-Instruct-7B) plus a ~0.3M residual policy on P2′ scores. Code EgorShibaev/remarl released as of 2026-11-18. Distinct slug remar from method:tdlm.'
last_reviewed: '2026-11-18'
papers:
- paper:remar
recipes:
- recipe:remar
claims:
- benchmark: 'LLaDA-8B-Instruct GSM8K NFE8 vs P2′'
  metric: 'accuracy'
  value: '53.60 vs P2′ τ=1 28.76 (+24.84) and vs calibrated P2′ τ=0.25 42.30 (+11.30)'
  baseline: 'P2′ τ=1 / temperature-calibrated P2′ τ=0.25'
  date: '2026-11-18'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.22576'
  notes: 'Does not retarget method:a2d / method:tdlm / method:forkgrpo. Mention on task:continuous-diffusion-lm-pretrain. Code EgorShibaev/remarl.'
tags:
- dllm
- remasking
- grpo
- active
---

# ReMaRL

## Method Overview
ReMaRL trains a ~0.3M GRPO policy that residual-corrects P2′ confidence scores to choose which positions to unmask, retain, or remask. The diffusion LM stays frozen. P2′ itself (current-token scoring plus temperature) is the no-train baseline.

## When to Use
- Frozen discrete dLLM decoding when heuristic unmask/remask order leaves accuracy on the table at a fixed NFE.

## When NOT to Use
AR-delta recycle remains `method:a2d`. Frozen hidden-history self-conditioning remains `method:tdlm`. Entropy-fork dLLM RL remains `method:forkgrpo`. Continuous pretrain remains `method:semicat`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:diffusion-lm-ar-delta-recycle`. Mention on `task:continuous-diffusion-lm-pretrain`. Does **not** replace A2D, TDLM, or ForkGRPO.

## Gotchas & Failure Modes
- Distinct slug `remar` from `method:tdlm`.
- Train a separate policy per NFE; reusing a larger-budget checkpoint is the paper's transfer curve, not the main claim.
- Bias-only training stays near untrained P2′ in the ablation.
