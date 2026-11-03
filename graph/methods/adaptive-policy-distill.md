---
id: method:adaptive-policy-distill
type: method
title: 'Adaptive-Policy Distillation'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'same-tokenizer single-teacher matching distillation'
  reason: 'OPD remains matching; APD is a knowledge-injection gate under information asymmetry'
  use_instead: method:opd
assumptions:
- 'Document-QA knowledge injection without labels or a verifier. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:adaptive-policy-distill
recipes:
- recipe:adaptive-policy-distill
claims:
- benchmark: 'QASPER / BioASQ document-QA knowledge injection'
  metric: 'F1 / MRR vs OPD'
  value: 'up to +54.6% vs OPD; QASPER 0.558 F1; BioASQ 0.486 MRR'
  baseline: 'reverse-KL OPD and off-policy distillation'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.00852'
  notes: 'Does not retarget method:opd.'
tags:
- opd
- knowledge-injection
- active
---

# Adaptive-Policy Distillation

## Method Overview
APD is knowledge-injection OPD: a per-token gate mixes teacher-directed rollouts and forward KL only where student-teacher divergence concentrates, then anneals the intervention.

## When to Use
- Closed-book knowledge injection from documents where reverse-KL OPD under-lifts rare tokens.

## When NOT to Use
OPD remains same-tokenizer matching distillation. Open-MOPD remains multi-teacher.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd` or `method:open-mopd`.

## Gotchas & Failure Modes
- Knowledge-injection setting, not the library math-OPD bake-off.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
