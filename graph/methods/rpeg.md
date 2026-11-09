---
id: method:rpeg
type: method
title: 'RPEG (RLM Pipeline Execution Graph)'
category: training-systems
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'choosing the production frontier RL post-train engine'
  reason: 'Miles remains the production stack; RPEG is a graph IR plus planner for PPO/GRPO pipelines'
  use_instead: method:miles
- when: 'variable environment latency / async stragglers is the bottleneck'
  reason: 'SAO remains the async algorithm; RPEG plans bounded asynchrony inside a pipeline IR'
  use_instead: method:sao
- when: 'lossless overlap of GRPO/OPD gradient computation with rollout'
  reason: 'ThunderSyncRL is no-staleness overlap; RPEG is a planner/runtime IR'
  use_instead: method:thundersyncrl
- when: 'factory process / experiments-as-code / lineage rather than the RL engine'
  reason: 'Poolside is the factory; RPEG is pipeline IR'
  use_instead: method:poolside-model-factory
assumptions:
- 'Synchronous PPO comparison with separate actor and critic unless noted. Paper: up to 256 GH200 (Clariden) and A100 (Athena); Llama 3.1 8B / 3.3 70B vs verl; 7B–70B vs ReaL. No public code as of 2026-11-09. arXiv 2611.09207 above watermark 2611.08453.'
last_reviewed: '2026-11-09'
papers:
- paper:rpeg
recipes:
- recipe:rpeg
claims:
- benchmark: 'GH200 vs verl (Llama 3.1 8B / 3.3 70B, separate actor/critic) and A100 vs ReaL (7B–70B)'
  metric: 'step time / throughput; accuracy vs verl'
  value: 'up to 2.477× lower step time vs verl (median 1.488×); up to 2× vs ReaL; utilization +30%; accuracy within 0.47% of verl'
  baseline: 'verl / ReaL / fully colocated input plans'
  date: '2026-11-09'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.09207'
  notes: 'Does not retarget method:miles. Optimized synchronous plans are 1.250–1.471× vs executable fully colocated inputs.'
tags:
- systems
- rl
- post-training
- active
---

# RPEG (RLM Pipeline Execution Graph)

## Method Overview
RPEG is a data-centric graph IR for RLM PPO/GRPO pipelines. One plan jointly chooses pipeline structure (bounded asynchrony, actor–critic sharing) and execution (stage fusion, scheduling, multi-dimensional parallelism) under an analytical cost model of compute, communication, memory, and rack/node/GPU hierarchy.

## When to Use
- Scaling a PPO/GRPO training pipeline across many GPUs when placement, fusion, and asynchrony interact and a production Miles-style engine is not the constraint.

## When NOT to Use
Production engine remains `method:miles`. Async straggler algorithm remains `method:sao`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:frontier-rl-posttrain-stack`. Does **not** replace Miles.

## Gotchas & Failure Modes
- No public code.
- Reported speedups are synchronous PPO with separate actor and critic unless an ablation names AC sharing / bounded asynchrony.
