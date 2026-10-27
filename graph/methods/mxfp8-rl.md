---
id: method:mxfp8-rl
type: method
title: 'MXFP8 RL Matching'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:fp4-rl-train-rollout-alignment'
  reason: 'TRACE/TRIAGE remain dual-active NVFP4 hops; this card is MXFP8 train-rollout grid matching on Blackwell'
  use_instead: method:trace
- when: 'native NVFP4 RL execution alignment (miniTE)'
  reason: 'miniTE is NVFP4 execution; this card is MXFP8 matching'
  use_instead: method:minite
assumptions:
- 'MXFP8 RL in verl (Megatron/TE train; vLLM/SGLang rollout) on B200. No dedicated repo as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:mxfp8-rl
recipes:
- recipe:mxfp8-rl
claims:
- benchmark: 'Qwen3-8B / Qwen3-30B-A3B MXFP8 RL on B200 vs BF16 sampler'
  metric: 'train-rollout KL; byte-equal weights'
  value: 'same-grid sampler KL -11% (half linears) / -16% (all); synchronized weights match the learner FP8 forward bytes'
  baseline: 'MXFP8 learner with BF16 sampler; off-grid FP8 sampler'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.34915'
  notes: 'Does not retarget method:trace, method:triage, or method:minite.'
tags:
- quantization
- rlvr
- active
---

# MXFP8 RL Matching

## Method Overview
MXFP8 RL matching puts the sampler on the learner's MXFP8 grid. A higher-precision BF16 sampler is less consistent than a matched low-precision one, and an off-grid FP8 sampler doubles KL on MoE.

## When to Use
- Blackwell MXFP8 RL where train and rollout disagree on the scale grid.

## When NOT to Use
Default on `task:fp4-rl-train-rollout-alignment` remains `method:trace` + `method:triage`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:trace` or `method:triage`.

## Gotchas & Failure Modes
- Not a replacement for `method:trace`.
- Matching can still fail when the sampler uses another FP8 grid.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
