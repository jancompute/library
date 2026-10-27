---
id: method:papo
type: method
title: 'PAPO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:multi-reward-rlvr'
  reason: 'CorrGRPO/DARA remain dual-active aggregation; PAPO preserves primary-advantage sign under an auxiliary reward'
  use_instead: method:corrgrpo
- when: 'single-turn dense math/code Pass@1 RLVR (one verifier reward)'
  reason: 'CISPO remains one-reward Pass@1'
  use_instead: method:cispo
assumptions:
- 'Primary/auxiliary multi-reward aggregation. Project page announced, no dedicated GitHub as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:papo
recipes:
- recipe:papo
claims:
- benchmark: 'Multi-reward GRPO/PPO vs additive aggregation'
  metric: 'primary objective under auxiliary conflict'
  value: 'keeps primary sign during fusion; best primary with competitive auxiliary across GRPO and PPO hosts'
  baseline: 'additive multi-reward aggregation; CorrGRPO / DARA'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.34862'
  notes: 'Does not retarget method:corrgrpo or method:dara.'
tags:
- rl-alignment
- multi-reward
- active
---

# PAPO

## Method Overview
PAPO fuses a primary and an auxiliary advantage so agreeing auxiliary distinctions survive and conflicting ones shrink, instead of letting a large auxiliary term flip the primary preference.

## When to Use
- Multi-reward RL where correctness (or another primary) must outrank length/style/efficiency auxiliaries.

## When NOT to Use
Default on `task:multi-reward-rlvr` remains `method:corrgrpo` + `method:dara`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:corrgrpo` or `method:dara`.

## Gotchas & Failure Modes
- Not a replacement for `method:corrgrpo`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
