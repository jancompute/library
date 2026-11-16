---
id: method:acerl
type: method
title: ACE-RL
category: agent-memory
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'write-time playbook agent memory (ACE default)'
    reason: 'ACE remains the write-time playbook; ACE-RL freezes the ACE harness and co-optimizes actor/reflector/curator'
    use_instead: method:ace
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift or rubric credit)'
    reason: 'CANOPY remains checker coverage; ACE-RL rewards handoff artifacts by a downstream actor rollout'
    use_instead: method:canopy
assumptions:
  - 'Fix the ACE harness. Co-optimize actor, reflector, and curator with per-role GRPO groups. Reward handoff artifacts by a downstream actor rollout. Qwen3-0.6B / Qwen3-4B-Instruct-2507. No public code as of 2026-11-16 (`code_status: none`).'
last_reviewed: '2026-11-16'
papers:
- paper:acerl
recipes:
- recipe:acerl
claims:
- benchmark: 'Qwen3-4B-Instruct AppWorld / MiniSWEBench / Mastermind / MBPP RSI@3 vs GRPO-in-harness pass@3'
  metric: 'RSI@3 vs GRPO pass@3'
  value: 'AppWorld 0.667 vs 0.60; MiniSWEBench 0.340 vs 0.26; Mastermind 0.775 vs 0.74; MBPP 0.987 vs 0.82; deltas +0.042 / +0.095 / +0.089 / +0.120'
  baseline: 'GRPO inside the frozen ACE harness'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.16409'
  notes: 'Does not retarget method:ace or method:canopy. HF Daily leftover. Distinct from method:hive-mem (read-time expansion).'
- benchmark: 'RSI@8 vs GRPO pass@8 on Mastermind / MBPP / AppWorld / MiniSWEBench'
  metric: 'RSI@8 vs pass@8'
  value: '0.81 / 0.99 / 0.81 / 0.40 vs GRPO 0.78 / 0.91 / 0.68 / 0.30'
  baseline: 'GRPO pass@8 inside the same harness'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.16409'
  notes: 'Experience-handoff RL. No public code.'
tags:
- agent-memory
- grpo
- rsi
- active
---

# ACE-RL

## Method Overview
ACE-RL (Experience-Handoff RL) keeps the ACE harness frozen and co-optimizes the actor, reflector, and curator. Handoff artifacts are rewarded by a downstream actor rollout, not by a playbook edit reward. Per-role GRPO groups stop one role from eating another's credit.

## When to Use
- ACE-style memory when the playbook is already the harness and the missing piece is co-training the roles that write and use it.

## When NOT to Use
Write-time playbook default remains `method:ace`. Sparse-outcome coverage remains `method:canopy`. Multimodal expansion remains `method:hive-mem`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:agent-memory`. Mention on `task:outcome-only-long-horizon-agent-rl`. Does **not** replace ACE or CANOPY.

## Gotchas & Failure Modes
- Freezes ACE; it does not replace ACE as the memory default.
- No public code as of 2026-11-16 (`code_status: none`).
