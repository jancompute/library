---
id: method:li2sao
type: method
title: 'Li2SAO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agentic-async-rl'
  reason: 'SAO remains async straggler replay; Li2SAO bootstraps a light critic then switches to single-rollout GAE'
  use_instead: method:sao
assumptions:
- 'Async single-rollout RL without a pretrained value model. Official code jd-cc-coder/Li2SAO on slime.'
last_reviewed: '2026-11-02'
papers:
- paper:li2sao
recipes:
- recipe:li2sao
claims:
- benchmark: 'Single-turn reasoning and multi-turn agentic async RL vs GRPO / LiSAO'
  metric: 'early-training catch-up and later ceiling without a pretrained critic'
  value: 'catches or surpasses GRPO early; raises later agentic ceiling vs LiSAO'
  baseline: 'GRPO; LiSAO (SAO without pretrained value model)'
  date: '2026-11-02'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.40726'
  notes: 'Does not retarget method:sao.'
tags:
- async-rl
- actor-critic
- active
---

# Li2SAO

## Method Overview
Li2SAO lifts light single-rollout async RL by group-relative actor-critic bootstrapping: while the critic is cold, group-relative advantage updates the actor and group-centered return updates the critic, then training switches to single-rollout GAE.

## When to Use
- Async single-rollout agentic RL when you cannot use SAO's closed-source pretrained value model.

## When NOT to Use
SAO remains the async straggler first hop.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:sao`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-11-02; no locked-SOTA bake-off.
- The bootstrap is a critic-warmup, not a replacement for SAO's straggler replay.
