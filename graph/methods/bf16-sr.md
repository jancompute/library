---
id: method:bf16-sr
type: method
title: 'BF16+SR (Stochastic Rounding on FP32→BF16 Cast)'
category: systems
status: active
sota_for: []
supersedes: []
do_not_use_for:
    - when: 'unbiased fp32 to bf16 export of the served copy'
      reason: 'Fair Cast is export-time unbiased cast; BF16+SR is train-time SR of the FP32 shadow used for RL rollouts'
      use_instead: method:fair-cast
    - when: 'rounding-location alignment between inference and train for RL'
      reason: 'Rounding-Align RL matches rounding sites; BF16+SR is SR when writing the BF16 copy'
      use_instead: method:rounding-align-rl
    - when: '~7B dense pretrain optimizer default'
      reason: 'Muon2 remains the optimizer; BF16+SR is a cast rule. Pretrain BF16 already matches FP32; this gap is RLVR at low LR'
      use_instead: method:muon2
assumptions:
    - 'FP32 shadow weights quantized to BF16 for rollout and train at typical RLVR LRs (~1e-6). NVIDIA. No public standalone trainer as of 2026-11-11. arXiv 2611.13545 above watermark 2611.12886. Sibling of Fair Cast / Rounding-Align RL / DLC. Distinct from paper:weight-update-leverage (bf16 freeze without fp32 master).'
last_reviewed: '2026-11-11'
papers:
- paper:bf16-sr
recipes:
- recipe:bf16-sr
claims:
- benchmark: 'DeepSeek-R1-Distill-Qwen-1.5B/14B and Qwen3-30B-A3B RLVR (MATH-1460 / DAPO-Math-17k)'
  metric: 'reward trajectory vs FP16 / RN-BF16'
  value: 'BF16+SR matches FP16 convergence speed; raising BF16 LR also matches speed but increases KL vs the reference; SR in the forward passes alone is sufficient'
  baseline: 'round-to-nearest BF16 / FP16 / higher-LR BF16'
  date: '2026-11-11'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.13545'
  notes: 'Does not retarget method:fair-cast, method:muon2, or TRACE/TRIAGE. Gap remains when rollout and train logp are bit-exact, so it is not train–infer mismatch. No FP16 loss scaling.'
tags:
- systems
- bf16
- stochastic-rounding
- rlvr
- active
---

# BF16+SR (Stochastic Rounding on FP32→BF16 Cast)

## Method Overview
At RLVR learning rates, round-to-nearest BF16 sticks: small FP32 shadow updates often leave the BF16 weights used for rollout and train unchanged for several steps (BF16 ULP is $8\times$ FP16). Stochastic rounding when quantizing the shadow to BF16 matches FP16's reward trajectory without FP16 loss scaling and with less KL drift than raising the BF16 LR. Forward-pass SR is enough. This is not train–infer mismatch: the gap remains when backends agree bit-exactly.

## When to Use
- Mixed-precision RLVR with an FP32 shadow and a BF16 served/rollout copy at $\sim 10^{-6}$ LR.

## When NOT to Use
Export-time unbiased cast remains `method:fair-cast`. Rounding-site RL alignment remains `method:rounding-align-rl`. The ~7B optimizer remains `method:muon2`. Pretrain BF16 already matches FP32; do not apply this as a pretrain default.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:fp4-rl-train-rollout-alignment`. Mentions on `task:frontier-rl-posttrain-stack` and `task:llm-pretraining-optimization`. Does **not** replace Fair Cast, TRACE/TRIAGE, or Muon2.

## Gotchas & Failure Modes
- No public standalone trainer (`code_status: none`).
- Distinct from `paper:weight-update-leverage` (bf16 freeze without an fp32 master).
- SR is not a substitute for matching train/infer rounding sites in NVFP4 RL.
