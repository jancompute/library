---
id: method:loco
type: method
title: 'LoCo'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; LoCo is a continue-vs-conclude length plug-in'
  use_instead: method:cispo
assumptions:
- 'Frozen-prefix local DPO on a GRPO/CISPO host. Sibling of When2Think / LSD. Code released as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:loco
recipes:
- recipe:loco
claims:
- benchmark: 'math / code RLVR length'
  metric: 'completion length reduction'
  value: 'math −41.7% to −45.4%; code −23.4% to −36.3%'
  baseline: 'unmodified GRPO/CISPO-family traces'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.04814'
  notes: 'Does not retarget method:cispo. Sibling of method:when2think / method:lsd.'
tags:
- rlvr
- length
- active
---

# LoCo

## Method Overview
LoCo learns a local continue-vs-conclude preference from frozen prefixes so long RLVR traces stop earlier.

## When to Use
- Pass@1 math/code RLVR whose traces are too long and When2Think / LSD are not already in the stack.

## When NOT to Use
CISPO remains Pass@1. This is a length plug-in, not a loss.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`. Sibling of `method:when2think` and `method:lsd`.

## Gotchas & Failure Modes
- Local DPO, not a replacement of the group RLVR update.
