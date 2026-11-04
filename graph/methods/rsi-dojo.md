---
id: method:rsi-dojo
type: method
title: 'RSI-Dojo'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agentic-rsi-routing-posttrain'
  reason: 'NeoHorse-1 remains routing-guided OPD; RSI-Dojo is a post-train env suite'
  use_instead: method:neohorse-1
assumptions:
- 'SFT on RSI-Craft envs, not a routing-harness OPD recipe. No public code as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:rsi-dojo
recipes:
- recipe:rsi-dojo
claims:
- benchmark: 'PostTrainBench Lite'
  metric: 'SFT gain on Qwen3.5-9B / Qwen3.6-35B-A3B'
  value: '+8.74 / +16.87 (29.95 / 53.29 Lite)'
  baseline: 'unadapted Qwen3.5-9B / Qwen3.6-35B-A3B'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03698'
  notes: 'Does not retarget method:neohorse-1.'
tags:
- rsi
- post-training
- active
---

# RSI-Dojo

## Method Overview
RSI-Dojo is a suite of 281 post-train environments (RSI-Craft) for teaching a model to run SFT/RL loops rather than a new routing-guided OPD recipe.

## When to Use
- You need RSI post-train *environments* before or beside NeoHorse-1 routing-guided OPD.

## When NOT to Use
NeoHorse-1 remains the routing-harness post-train first hop. omp2 remains the production kernel.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:neohorse-1`.

## Gotchas & Failure Modes
- Env suite, not a trainer.
- No public code as of 2026-11-04.
