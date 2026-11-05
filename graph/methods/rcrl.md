---
id: method:rcrl
type: method
title: 'RcRL (Rubric Curriculum RL)'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'a programmatic checker exists and sparse outcome RL is enough'
  reason: 'CANOPY remains the checker-exists first hop; RcRL is pairwise rubric curriculum for non-verifiable domains'
  use_instead: method:canopy
- when: 'single-turn math/code Pass@1 RLVR'
  reason: 'CISPO remains Pass@1; RcRL is open-ended rubric RL'
  use_instead: method:cispo
assumptions:
- 'No new labeled data, human annotations, or stronger teacher. Pairwise preferences plus a curriculum over rubric criteria. Sibling of DRACO / MetaRubric / CoCA / RACE. No public GitHub as of 2026-11-05.'
last_reviewed: '2026-11-05'
papers:
- paper:rcrl
recipes:
- recipe:rcrl
claims:
- benchmark: 'Qwen3-4B creative writing / HealthBench'
  metric: 'human win rate vs base; HealthBench full / consensus lift'
  value: '70.5% human win; HealthBench +14.60% / +25.38% vs RaR +8.26% / +7.53%'
  baseline: 'absolute-score rubric RL / instance-specific rubrics / RaR'
  date: '2026-11-05'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.06244'
  notes: 'FictionBench keeps climbing past 1000 steps while RaR plateaus. Does not retarget method:canopy or method:draco.'
tags:
- rubric-rl
- curriculum
- open-ended
- active
---

# RcRL (Rubric Curriculum RL)

## Method Overview
RcRL exploits the generation-verification gap in non-verifiable domains. The same model judges pairwise rollout preferences, and new rubric criteria are introduced when current ones stop moving, so the objective does not stay stationary. Absolute rubric scores plateaus; pairwise plus curriculum keeps entropy and keeps climbing.

## When to Use
- Open-ended post-train (creative writing, health QA, rubric-judged advice) with no checker and no extra labeled data.

## When NOT to Use
CANOPY when a programmatic checker exists. CISPO for labeled math/code. DRACO remains the library's outcome-blind AppWorld rubric sibling.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:outcome-only-long-horizon-agent-rl`. Does **not** replace `method:canopy` or `method:draco`. Sibling of `method:metarubric`, `method:coca`, and `method:race-rubric`.

## Gotchas & Failure Modes
- Pairwise judge and generator share a model; curriculum is what stalls reward hacking, not a stronger teacher.
- No public code as of 2026-11-05.
