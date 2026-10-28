---
id: method:concur
type: method
title: 'CONCUR'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:multi-reward-rlvr'
  reason: 'CorrGRPO / DARA remain the multi-reward first hop; CONCUR projects gated-auxiliary scores so they cannot reverse the primary'
  use_instead: method:corrgrpo
- when: 'priority-preserving primary/auxiliary advantage fusion (PAPO)'
  reason: 'PAPO fuses advantages with priority; CONCUR projects gated-auxiliary standardized scores'
  use_instead: method:papo
assumptions:
- 'Multi-task RL with a primary reward that gates auxiliaries such as length. CONCUR-T vs CONCUR-A. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:concur
recipes:
- recipe:concur
claims:
- benchmark: 'Multi-task, multi-reward LLM RL with gated auxiliaries'
  metric: 'primary-order preservation; task-wise win/loss vs keeping or dropping gated auxiliaries'
  value: 'replaces gated-auxiliary standardized scores with the closest scores that cannot reverse the primary order, with ceiling ties; CONCUR-T keeps both constraints, CONCUR-A lifts the ceiling-tie for an auxiliary that should still rank at the primary ceiling'
  baseline: 'group-relative advantages on gated auxiliaries; drop-auxiliary vs keep-auxiliary'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36437'
  notes: 'Does not retarget method:corrgrpo.'
tags:
- rl-alignment
- multi-reward
- active
---

# CONCUR

## Method Overview
CONCUR projects each gated auxiliary's standardized scores onto the nearest vector that is monotone in the primary reward and constant at the primary ceiling, so an auxiliary cannot flip the group's primary order.

## When to Use
- Multi-reward GRPO where a gated length/format auxiliary reverses the primary on failures, but dropping it hurts other tasks.

## When NOT to Use
Default on `task:multi-reward-rlvr` remains `method:corrgrpo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:corrgrpo`.

## Gotchas & Failure Modes
- Not a replacement for `method:corrgrpo`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
