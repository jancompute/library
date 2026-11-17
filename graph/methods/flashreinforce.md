---
id: method:flashreinforce
type: method
title: FlashREINFORCE
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'variable environment latency / async stragglers'
    reason: 'SAO remains the async algorithm; FlashREINFORCE is critic-free one-rollout REINFORCE, not straggler replay'
    use_instead: method:sao
  - when: 'CEM-style critic-free RFT from replay when group rollouts are impractical'
    reason: 'FTW is replay CEM; FlashREINFORCE is live one-pass REINFORCE with a sequence trust region'
    use_instead: method:ftw
  - when: 'async single-rollout SWE recipe (Muon + token-avg loss + truncated IS)'
    reason: 'muon-lh-rl is a Muon/IS SWE recipe; FlashREINFORCE is One-Batch REINFORCE + Sequence Trust Region + Sample-Mean Optimization'
    use_instead: method:muon-lh-rl
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; FlashREINFORCE is a critic-free one-rollout async trainer, not the dense loss'
    use_instead: method:cispo
assumptions:
  - 'One rollout per prompt. Hosts: DeepSeek-R1-Distill-Qwen-1.5B lag ~4 through 6k updates; Qwen2.5-Math-1.5B 256k rollouts; Qwen3-30B-A3B Python-tool lag 8; Qwen2.5-7B-Instruct ALFWorld. Code in NVIDIA-NeMo/labs-molt (examples/scripts/quick_start/rl_flash_reinforce_r1d_1p5b.sh). Distinct from method:flash-opd.'
last_reviewed: '2026-11-17'
papers:
- paper:flashreinforce
recipes:
- recipe:flashreinforce
claims:
- benchmark: 'Qwen2.5-Math-1.5B five-benchmark mean; DeepSeek-R1-Distill-Qwen-1.5B async lag; Qwen2.5-7B-Instruct ALFWorld; Qwen3-30B-A3B Python-tool'
  metric: 'mean accuracy; updates at lag; seen/unseen success; lag'
  value: '38.0 mean vs GRPO +1.7 at 256k vs 512k rollouts; stable 6,000 updates at lag ~4; ALFWorld 98.3%/96.5% seen/unseen and keeps tool use where GRPO stops calling; 30B-A3B stable at lag 8'
  baseline: 'GRPO group-relative (k>1) at matched or doubled rollout budget'
  date: '2026-11-17'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.18627'
  notes: 'Does not retarget method:sao / method:cispo / method:ftw / method:muon-lh-rl. Distinct from method:flash-opd. Code NVIDIA-NeMo/labs-molt.'
tags:
- async-rl
- reinforce
- critic-free
- active
---

# FlashREINFORCE

## Method Overview
FlashREINFORCE is critic-free one-pass RL: One-Batch REINFORCE, a Sequence Trust Region, and Sample-Mean Optimization. One rollout per prompt keeps prompt coverage and removes group-sync barriers. The trust region and sample-mean step control policy drift and length-amplified negative updates on stale variable-length traces.

## When to Use
- Async agentic RL where group sampling wastes the budget on repeated prompts and you can take one rollout per prompt.

## When NOT to Use
Async stragglers remain `method:sao`. Pass@1 remains `method:cispo`. Replay CEM remains `method:ftw`. SWE Muon+IS remains `method:muon-lh-rl`. Adaptive OPD horizon remains `method:flash-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:agentic-async-rl`. Mention on `task:math-code-rl-dense`. Does **not** replace SAO, CISPO, FTW, or muon-lh-rl.

## Gotchas & Failure Modes
- Group-relative baselines are gone; the sequence trust region is load-bearing.
- Distinct slug from `method:flash-opd`.
