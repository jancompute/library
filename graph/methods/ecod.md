---
id: method:ecod
type: method
title: ECOD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift)'
    reason: 'CANOPY remains sparse-outcome coverage; ECOD is experience-calibrated teacher-weighting on OPD'
    use_instead: method:canopy
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains matching; ECOD reweights teacher losses by student experience'
    use_instead: method:opd
  - when: 'failure-only LCS action-sequence OPD'
    reason: 'LCS-OPD is failure-only action LCS; ECOD is temporal experience calibration on multi-turn OPD'
    use_instead: method:lcs-opd
assumptions:
  - 'Multi-turn agents with a teacher. Weights teacher losses or teacher-derived advantages from student-teacher trajectory comparison plus a temporal prior from successful teacher lengths. Qwen2.5-1.5B-Instruct / 7B-Instruct on ALFWorld and WebShop. No public code as of 2026-11-17.'
last_reviewed: '2026-11-17'
papers:
- paper:ecod
recipes:
- recipe:ecod
claims:
- benchmark: 'ALFWorld unseen / WebShop, Qwen2.5-1.5B-Instruct and 7B-Instruct, matched teachers'
  metric: 'relative success vs standard OPD; paired relative gains on SOD / TCOD-F2B / ATOD'
  value: 'up to +4.06% relative ALFWorld unseen vs OPD; average paired +6.20% ALFWorld unseen / +7.05% WebShop (WebShop 2.29% to 21.60%)'
  baseline: 'standard OPD and SOD / TCOD-F2B / ATOD without experience calibration'
  date: '2026-11-17'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.18656'
  notes: 'Does not retarget method:canopy / method:opd. Reusable weight on several distill objectives.'
tags:
- opd
- multi-turn
- agent
- active
---

# ECOD

## Method Overview
ECOD (Experience-Calibrated On-Policy Distillation) compares student and teacher multi-turn traces and builds a temporal prior from successful teacher lengths. The resulting weight multiplies teacher losses or teacher-derived advantages so supervision concentrates where the student still needs it.

## When to Use
- Multi-turn agent OPD when a uniform teacher loss over-supervises already-solved prefixes.

## When NOT to Use
Coverage RL remains `method:canopy`. Text matching remains `method:opd`. Failure-only LCS remains `method:lcs-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:outcome-only-long-horizon-agent-rl`. Mention on `task:student-distillation`. Does **not** replace CANOPY or OPD.

## Gotchas & Failure Modes
- The weight is a prior from teacher success length; a badly calibrated length prior can starve late turns.
- No public trainer as of 2026-11-17 (`code_status: none`).
