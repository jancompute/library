---
id: method:ep-opd
type: method
title: 'EP-OPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'same-tokenizer single-teacher matching distillation'
  reason: 'OPD remains matching; EP-OPD is evidence-paired document QA'
  use_instead: method:opd
assumptions:
- 'Scientific-document QA with matched counterfactual documents. Official code RuoranXu/EP-OPD.'
last_reviewed: '2026-11-03'
papers:
- paper:ep-opd
recipes:
- recipe:ep-opd
claims:
- benchmark: 'QASPER Qwen3-4B; PeerQA directional replica'
  metric: 'original / counterfactual accuracy / bypass'
  value: 'OPD +3.4 / -5.3 / +15.7 bypass; EP-OPD recovers 54-66% of counterfactual loss and 80-85% of original-doc gain'
  baseline: 'standard OPD on original documents'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.01967'
  notes: 'Code RuoranXu/EP-OPD. Does not retarget method:opd.'
tags:
- opd
- evidence
- active
---

# EP-OPD

## Method Overview
EP-OPD trains OPD on matched documents that support different answers to the same question, with a margin that favors each document's supported answer.

## When to Use
- Document-QA OPD where original-doc accuracy rises but the student ignores changed evidence.

## When NOT to Use
OPD remains matching distillation without an evidence-control requirement.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Bypass grows with the student's pre-distillation closed-book preference.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
