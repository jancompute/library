---
id: method:setgrpo
type: method
title: 'SetGRPO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:multi-reward-rlvr'
  reason: 'CorrGRPO / DARA remain the multi-reward aggregation first hop; SetGRPO calibrates grader-noise coefficient sets on rubric GRPO'
  use_instead: method:corrgrpo
- when: 'single-turn dense math/code Pass@1 RLVR'
  reason: 'CISPO remains Pass@1; SetGRPO is grader-uncertainty calibration on rubric groups'
  use_instead: method:cispo
assumptions:
- 'Rubric GRPO with grader randomness. Ten open-ended benches on Qwen3.5 and Llama3.2. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:setgrpo
recipes:
- recipe:setgrpo
claims:
- benchmark: 'Ten open-ended rubric RL benches on Qwen3.5 and Llama3.2'
  metric: 'macro average vs compared training methods'
  value: 'highest macro average among compared training methods on both Qwen3.5 and Llama3.2 families'
  baseline: 'GRPO with uncalibrated grader scores'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36807'
  notes: 'Does not retarget method:corrgrpo.'
tags:
- rl-alignment
- multi-reward
- grpo
- active
---

# SetGRPO

## Method Overview
SetGRPO builds a joint uncertainty set over GRPO training coefficients, maps candidates into the local update geometry, and risk-gates which group updates to keep so grader noise cannot reverse the group's direction.

## When to Use
- Rubric / grader RLVR where score jitter changes the whole group's GRPO coefficients, not just one reward margin.

## When NOT to Use
Default on `task:multi-reward-rlvr` remains `method:corrgrpo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:corrgrpo`.

## Gotchas & Failure Modes
- Not a replacement for `method:corrgrpo`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
