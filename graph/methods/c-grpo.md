---
id: method:c-grpo
type: method
title: 'C-GRPO (Conformal Group Relative Policy Optimization)'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; C-GRPO is a conformal adaptive group-size plug-in on GRPO'
  use_instead: method:cispo
assumptions:
- 'NeurIPS 2026. Sibling of NGU / ThinkPrior / AdaRoll-GRPO. Distinct from THUDM/CaRR citation-aware C-GRPO. Code released AryaFayyazi/CGRPO; pip install trl-cgrpo.'
last_reviewed: '2026-11-05'
papers:
- paper:c-grpo
recipes:
- recipe:c-grpo
claims:
- benchmark: 'Qwen2.5-7B-Instruct / Llama-3.1-8B GRPO, six math/science/code benches'
  metric: 'mean training rollouts vs G=32; pass@1'
  value: '49–70% fewer rollouts at matched pass@1; Llama-3.1-8B GSM8K up to 82% savings'
  baseline: 'fixed-budget GRPO G=32 / heuristic adaptive group size'
  date: '2026-11-05'
  verified: true
  evidence_level: peer-reviewed
  source_url: 'https://arxiv.org/abs/2611.05591'
  notes: 'NeurIPS 2026. Accuracy deltas sit in binomial noise. Does not retarget method:cispo. Distinct from citation-aware C-GRPO in THUDM/CaRR.'
tags:
- rlvr
- conformal
- adaptive-budget
- active
---

# C-GRPO (Conformal Group Relative Policy Optimization)

## Method Overview
C-GRPO replaces GRPO's fixed group size with split-conformal stopping over task-specific nonconformity scores. Closed-form reasoning uses APS-style prediction sets; execution-based code uses a first-success score. Miscoverage is selected automatically and thresholds are recalibrated as the policy moves. Easy prompts exit early; compute moves onto the hard tail.

## When to Use
- Dense math/code GRPO-family training where a fixed G wastes rollouts on easy prompts and a heuristic stop is not enough.

## When NOT to Use
CISPO remains Pass@1. This is a group-size plug-in, not a loss. Do not confuse with citation-aware C-GRPO.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`. Sibling of `method:ngu`, `method:thinkprior`, and `method:adaroll-grpo`.

## Gotchas & Failure Modes
- Pass@1 is matched, not a CISPO bake-off.
- Recalibration assumes the policy is not moving faster than the conformal split.
