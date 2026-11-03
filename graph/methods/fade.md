---
id: method:fade
type: method
title: 'FADE'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; FADE is a prompt scheduler'
  use_instead: method:cispo
assumptions:
- 'Group RLVR with binary rollout outcomes. Distinct from ThinkPrior / NGU / AdaRoll-GRPO. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:fade
recipes:
- recipe:fade
claims:
- benchmark: 'online group RLVR scheduling'
  metric: 'informative-group yield vs EMA/Beta pass-rate trackers'
  value: 'bilinear filter transfers ability shifts via rank-K Woodbury; item intercepts stay slow'
  baseline: 'per-prompt EMA or Beta pass-rate schedulers'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03625'
  notes: 'Does not retarget method:cispo. Distinct from method:thinkprior / method:ngu / method:adaroll-grpo.'
tags:
- rlvr
- scheduling
- active
---

# FADE

## Method Overview
FADE schedules RLVR prompts by separating policy ability from item difficulty so short memory does not scramble prompt order and long memory does not go stale.

## When to Use
- Online RLVR where silent groups burn budget and a single EMA pass-rate tracker is stale or noisy.

## When NOT to Use
CISPO remains Pass@1. ThinkPrior / NGU / AdaRoll-GRPO stay sibling schedulers.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Scheduler, not a loss.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
