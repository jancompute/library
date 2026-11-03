---
id: method:oc-opd
type: method
title: 'OC-OPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'same-tokenizer single-teacher matching distillation'
  reason: 'OPD remains matching; OC-OPD coordinates reverse/forward KL observations'
  use_instead: method:opd
assumptions:
- 'Heterogeneous student settings (non-thinking, thinking, base init). Official code RuoranXu/OC-OPD.'
last_reviewed: '2026-11-03'
papers:
- paper:oc-opd
recipes:
- recipe:oc-opd
claims:
- benchmark: 'math reasoning plus OOD scientific QA and code, three student settings'
  metric: 'accuracy vs OPD-family mixes'
  value: 'strong gains vs reverse/forward KL mixes in the paper; OOD transfer holds'
  baseline: 'reverse-KL and forward-KL OPD without observation bargaining'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.01965'
  notes: 'Code RuoranXu/OC-OPD. Does not retarget method:opd.'
tags:
- opd
- kl
- active
---

# OC-OPD

## Method Overview
OC-OPD coordinates reverse-KL and forward-KL OPD via a four-observation matrix and a closed-form bargain over logit gradients.

## When to Use
- Single-teacher OPD where reverse and forward KL should share a descent direction rather than be hand-mixed.

## When NOT to Use
OPD remains the matching default. Open-MOPD remains multi-teacher.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd` or `method:open-mopd`.

## Gotchas & Failure Modes
- Paper math/code numbers are not the library OPD bake-off.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
