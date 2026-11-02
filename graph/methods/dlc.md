---
id: method:dlc
type: method
title: 'DLC (Discrepancy-Lag Correction)'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:fp4-rl-train-rollout-alignment'
  reason: 'TRACE / TRIAGE remain FP4 train-rollout first hops; DLC splits numerical discrepancy from policy lag'
  use_instead: method:trace
- when: 'unbiased fp32 to bf16 export of the served copy (Fair Cast)'
  reason: 'Fair Cast fixes round-to-nearest export; DLC corrects discrepancy vs lag after sampling'
  use_instead: method:fair-cast
assumptions:
- 'Disaggregated sampler/trainer RL. Official code Skylanding/Training-Inference-Mismatch.'
last_reviewed: '2026-11-02'
papers:
- paper:dlc
recipes:
- recipe:dlc
claims:
- benchmark: 'Stale-sampler LLM RL on Qwen3-0.6B / 1.7B vs per-token IS / KL-on-sampler-prefix'
  metric: 'KL to on-policy training; collapse prevention'
  value: 'KL within 2x two independent on-policy runs; ESS<0.5 resync prevents collapses IS leaves'
  baseline: 'per-token mismatch corrections; KL measured on sampler prefixes'
  date: '2026-11-02'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.40945'
  notes: 'Does not retarget method:trace. Mention on task:agentic-async-rl.'
tags:
- rl
- numerics
- active
---

# DLC (Discrepancy-Lag Correction)

## Method Overview
DLC splits sampled-token error into a nearly constant numerical discrepancy and a trainer policy lag. Center the discrepancy, clip the lag ratio against the sampler weights, and resynchronize the sampler when the lag-ratio ESS falls below 0.5.

## When to Use
- Disaggregated RL where IS or prefix-KL corrections still collapse under stale weights.

## When NOT to Use
Default on `task:fp4-rl-train-rollout-alignment` remains `method:trace`. SAO remains async stragglers.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:trace` or `method:sao`. Distinct from `method:fair-cast` and `method:rounding-align-rl`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-11-02; no locked-SOTA bake-off.
- IS fails at the step where lag-ratio ESS drops below one half; DLC's resync is the load-bearing piece.
