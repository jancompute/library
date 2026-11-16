---
id: method:sebo
type: method
title: SEBO
category: diffusion-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'recycle an AR post-training weight delta onto a converted dLLM'
    reason: 'A2D recycles an AR delta; SEBO is a full-block unbiased ELBO estimator for masked dLLM post-train'
    use_instead: method:a2d
  - when: 'AR→discrete-dLLM on-policy distillation (JustOPD), not a weight-delta recycle'
    reason: 'JustOPD is AR→dLLM on-policy distill; SEBO is variance-reduced MDLM ELBO post-train'
    use_instead: method:justopd
  - when: 'dLLM RL that forks from high-entropy intermediate states (ForkGRPO)'
    reason: 'ForkGRPO is GRPO-family dLLM RL; SEBO is an ELBO estimator'
    use_instead: method:forkgrpo
assumptions:
  - 'Masked diffusion LM post-train (LLaDA-8B-Instruct in the paper). Evaluate every block once per ELBO estimate. GitHub githubhyz/See_Every_Block_Once empty as of 2026-11-16 (`code_status: announced`). AACL-IJCNLP 2026.'
last_reviewed: '2026-11-16'
papers:
- paper:sebo
recipes:
- recipe:sebo
claims:
- benchmark: 'LLaDA-8B-Instruct GSM8K / MATH-500 / Countdown / Sudoku / HumanEval vs random-block ELBO (SPG)'
  metric: 'accuracy; 5-task avg vs random block'
  value: 'GSM8K 82.26, MATH-500 38.00, Sudoku 91.39 vs SPG 72.73, HumanEval 36.59; +12.79 avg vs random block; highest on 4/5'
  baseline: 'SPG / random-block ELBO sampling'
  date: '2026-11-16'
  verified: true
  evidence_level: peer-reviewed
  source_url: 'https://arxiv.org/abs/2611.17754'
  notes: 'Does not retarget method:a2d / method:justopd / method:forkgrpo. AACL-IJCNLP 2026. GitHub empty → announced.'
tags:
- dllm
- elbo
- post-training
- active
---

# SEBO

## Method Overview
SEBO (See Every Block Once) is a full-block unbiased ELBO estimator for masked diffusion LM post-train. Random block sampling is high-variance; SEBO evaluates every block once so the estimator is unbiased and lower-variance without changing the MDLM objective.

## When to Use
- Masked dLLM post-train when the ELBO is estimated by sampling denoising blocks.

## When NOT to Use
AR-delta recycle remains `method:a2d`. AR→dLLM on-policy distill remains `method:justopd`. dLLM entropy-fork RL remains `method:forkgrpo`. Image/flow reward alignment remains `method:diffusion-opsd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:diffusion-lm-ar-delta-recycle`. Does **not** replace A2D, JustOPD, or ForkGRPO.

## Gotchas & Failure Modes
- Estimator, not a new dLLM architecture or an AR weight-delta recycle.
- GitHub `githubhyz/See_Every_Block_Once` exists but is empty as of 2026-11-16 (`code_status: announced`).
