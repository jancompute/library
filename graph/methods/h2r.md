---
id: method:h2r
type: method
title: 'H2R'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; H2R adds hierarchical hint rewards'
  use_instead: method:cispo
assumptions:
- 'Problems with sub-question structure. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:h2r
recipes:
- recipe:h2r
claims:
- benchmark: 'HiMath hierarchical math RLVR vs outcome-only RLVR'
  metric: 'reasoning accuracy with/without task-specific training'
  value: 'hierarchical hints improve even without task-specific training'
  baseline: 'outcome-only RLVR; CoT prompting without structured hints'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.39934'
  notes: 'Does not retarget method:cispo.'
tags:
- rlvr
- hints
- active
---

# H2R

## Method Overview
H2R treats a math problem's sub-questions as hint-conditioned intermediate rewards during RLVR, so the policy is scored on reaching structured milestones rather than only the final box.

## When to Use
- Math RLVR with problems that already have a sub-question tree.

## When NOT to Use
CISPO remains Pass@1. RGPO is GT-rationale scaffolding, a different hint channel.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo` or `method:rgpo`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Needs hierarchically structured problems (HiMath).
- No public code as of 2026-10-30.
