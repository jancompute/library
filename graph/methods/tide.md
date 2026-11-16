---
id: method:tide
type: method
title: TIDE
category: training-systems
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'production post-train engine (SGLang / Megatron / LoRA RL / OPD)'
    reason: 'Miles remains the production engine; TIDE is colocated on-policy GPU reclaim'
    use_instead: method:miles
  - when: 'variable environment latency / async stragglers'
    reason: 'SAO remains the async algorithm; TIDE is colocated on-policy overlap, not off-policy straggler replay'
    use_instead: method:sao
  - when: 'lossless (no-staleness) overlap of GRPO/OPD gradient computation with rollout'
    reason: 'ThunderSyncRL is disaggregated lossless overlap; TIDE reclaims finished colocated rollout GPUs'
    use_instead: method:thundersyncrl
assumptions:
  - 'Colocated on-policy RL (DAPO-Math / Text2SQL). Megatron DP+TP or FSDP ZeRO. 4x L40S to 8x H200. No dedicated TIDE repo as of 2026-11-16 (`code_status: none`). Mentions THUDM/slime and ServingStudio.'
last_reviewed: '2026-11-16'
papers:
- paper:tide
recipes:
- recipe:tide
claims:
- benchmark: 'DAPO-Math / Text2SQL colocated on-policy RL, 4x L40S to 8x H200; Megatron DP+TP and FSDP ZeRO'
  metric: 'throughput vs colocated; fraction of optimal; GPU idle'
  value: 'up to 1.36× vs colocated; 77–97% of optimal; baseline GPU idle up to 30% plus inefficient decode 9.8%'
  baseline: 'colocated on-policy RL without reclaim; optimal disaggregated split'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.17924'
  notes: 'Does not retarget method:miles / method:sao / method:thundersyncrl. Barrier only before the weight update. Distinct from ThunderSyncRL (disaggregated lossless overlap).'
tags:
- rl-systems
- on-policy
- colocated
- active
---

# TIDE

## Method Overview
TIDE (Time-Interleaved Data-parallel Execution) reclaims finished colocated rollout GPUs for training and migrates remaining rollouts. The only barrier is before the weight update, so on-policy GRPO/DAPO stays on-policy. Colocated baselines waste idle GPUs (up to 30%) and inefficient decode (9.8%).

## When to Use
- Colocated on-policy RL when rollout GPUs finish before the trainer and you want to reclaim them without going off-policy.

## When NOT to Use
Production stack remains `method:miles`. Async stragglers remain `method:sao`. Disaggregated lossless overlap remains `method:thundersyncrl`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:frontier-rl-posttrain-stack`. Mention on `task:agentic-async-rl`. Does **not** replace Miles, SAO, or ThunderSyncRL.

## Gotchas & Failure Modes
- Colocated reclaim, not disaggregated streaming and not SAO off-policy replay.
- No dedicated TIDE GitHub as of 2026-11-16 (`code_status: none`). SyFI-ServingStudio/TIDE 404.
