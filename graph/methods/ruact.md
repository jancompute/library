---
id: method:ruact
type: method
title: 'RuACT (Rubrics as Adaptive Critics and Teachers)'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'a programmatic checker exists and sparse outcome RL is enough'
  reason: 'CANOPY remains checker coverage; RuACT recovers inactive rubric criteria'
  use_instead: method:canopy
- when: 'no programmatic checker exists and the reward must come from process criteria'
  reason: 'DRACO remains outcome-blind rubric credit; RuACT is inactive-rubric recovery on a GRPO host'
  use_instead: method:draco
- when: 'pairwise + rubric-criteria curriculum for non-verifiable domains (RcRL)'
  reason: 'RcRL is a curriculum over criteria; RuACT assigns Teacher vs Critic roles to inactive criteria'
  use_instead: method:rcrl
- when: 'learning rubric rewards for rubric-based RL (vacuous credit)'
  reason: 'MetaRubric learns the judge; RuACT reuses existing inactive rubrics'
  use_instead: method:metarubric
- when: 'gold-solution privileged OPSD as the trainer'
  reason: 'VISTA remains privileged-teacher first hop; RuACT uses unreachable rubrics as PI inside GRPO'
  use_instead: method:vista
assumptions:
- 'Query-specific rubrics on a GRPO host. Paper: Qwen3-1.7B/4B, RaR-Medicine/Science, verl, 200 steps, Qwen3-32B train judge / DeepSeek-V4.1-Flash eval judge, two A800. Code ZJU-REAL/RuACT released as of 2026-11-09. arXiv 2611.09597 above watermark 2611.08453.'
last_reviewed: '2026-11-09'
papers:
- paper:ruact
recipes:
- recipe:ruact
claims:
- benchmark: 'Qwen3-4B medical/science four-bench (RaR-Med / HealthBench / RaR-Sci / ResearchQA)'
  metric: 'avg / ResearchQA vs GRPO'
  value: 'avg 56.52→59.12; ResearchQA 64.82→69.44; HealthBench 37.62→40.12; 1.7B avg 45.04→47.17'
  baseline: 'GRPO / Reweight / RuscaRL'
  date: '2026-11-09'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.09597'
  notes: '60.88% inactive query–rubric observations (25.19% unreachable / 35.69% saturated). Does not retarget method:canopy / method:draco.'
tags:
- post-training
- rubric
- agentic
- active
---

# RuACT (Rubrics as Adaptive Critics and Teachers)

## Method Overview
When every rollout in a GRPO group fails a rubric (unreachable) or passes it (saturated), that criterion contributes no within-group contrast. RuACT assigns unreachable rubrics a Teacher role (privileged OPSD gated by a later unprivileged reward) and saturated rubrics a Critic role (child-rubric decomposition that restores contrast).

## When to Use
- Rubric GRPO where a large fraction of criteria are always-fail or always-pass inside the group.

## When NOT to Use
Checker-exists coverage remains `method:canopy`. Outcome-blind rubric credit remains `method:draco`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:outcome-only-long-horizon-agent-rl`. Sibling of `method:draco` / `method:metarubric` / `method:coca` / `method:race-rubric` / `method:rcrl`. Does **not** replace CANOPY or DRACO.

## Gotchas & Failure Modes
- Teacher guidance and child-rubric generation add inference cost beyond matched GRPO steps.
- Gains persist under a second judge (paper Appendix C); train and eval judges must stay distinct.
