---
id: method:agentic-opd
type: method
title: 'Agentic-OPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'choosing the single-teacher distillation algorithm'
  reason: 'OPD remains reverse-KL matching; Agentic-OPD mines discarded GRPO checkpoints'
  use_instead: method:opd
- when: 'choosing the multi-teacher distillation algorithm'
  reason: 'Open-MOPD remains labeled-teacher mix; Agentic-OPD has no domain teacher labels'
  use_instead: method:open-mopd
- when: 'outcome-only long-horizon agent RL (AppWorld coverage / anti-drift)'
  reason: 'CANOPY remains sparse-outcome coverage; Agentic-OPD is checkpoint-mined distill'
  use_instead: method:canopy
assumptions:
- 'A GRPO run that saved intermediate checkpoints. Paper: Qwen2.5-3B/7B, Qwen3-4B, DeepSearch/GAIA/HLE/xbench. Their DeepSearch protocol is not a harness ranking. No public code as of 2026-11-10. arXiv 2611.12799 above watermark 2611.09634.'
last_reviewed: '2026-11-10'
papers:
- paper:agentic-opd
recipes:
- recipe:agentic-opd
claims:
- benchmark: 'DeepSearch mean (Qwen2.5-3B / 7B / Qwen3-4B)'
  metric: 'mean accuracy vs GRPO'
  value: '47.3 / 54.4 / 50.4 vs GRPO 44.5 / 47.0 / 47.8; 4B vs GPT-5.6 25.4 / V4.1 42.7 (paper protocol)'
  baseline: 'GRPO / OPD / Open-MOPD / GKD / GPT-5.6 / DeepSeek-V4.1'
  date: '2026-11-10'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.12799'
  notes: 'Does not retarget method:opd, method:open-mopd, or method:canopy. DeepSearch numbers are not a harness ranking.'
tags:
- distillation
- opd
- agentic
- checkpoint-mining
- active
---

# Agentic-OPD

## Method Overview
Agentic-OPD distills from discarded GRPO checkpoints. HCN selects the teacher from token-level entropy and KL-to-init; LAD assigns per-layer teachers and drops layers whose KL would hurt.

## When to Use
- After a GRPO search-agent run, when intermediate checkpoints exist and vanilla OPD from the last checkpoint underfits.

## When NOT to Use
Single-teacher default remains `method:opd`. Multi-teacher default remains `method:open-mopd`. AppWorld coverage remains `method:canopy`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation` with a mention on `task:outcome-only-long-horizon-agent-rl`. Does **not** replace OPD, Open-MOPD, or CANOPY.

## Gotchas & Failure Modes
- No public trainer. Needs a checkpoint library from a completed GRPO run.
- 4B vs GPT-5.6 / V4.1 is their DeepSearch protocol, not OSWorld or SWE-bench ranking.
- Naive last-checkpoint OPD is weaker than HCN+LAD on the reported benches.
