---
id: method:ati-opd
type: method
title: 'ATI-OPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:student-distillation'
  reason: 'OPD remains matching; ATI-OPD splices teacher prefixes on long traces'
  use_instead: method:opd
assumptions:
- 'Same-tokenizer teacher logp. Long student responses. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:ati-opd
recipes:
- recipe:ati-opd
claims:
- benchmark: 'long-sequence OPD vs length control / loss reweighting'
  metric: 'training stability / downstream reasoning'
  value: 'repairs prefixes instead of discarding late tokens'
  baseline: 'length control; loss reweighting; fixed cutoffs'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.38160'
  notes: 'Does not retarget method:opd.'
tags:
- distillation
- opd
- active
---

# ATI-OPD

## Method Overview
ATI-OPD watches student-teacher disagreement along a long on-policy trace, splices a short teacher segment over the earliest high-disagreement span, and lets the student continue. Renewed disagreement triggers another splice. The prefix is repaired so later teacher logp stays on-policy.

## When to Use
- Long-CoT OPD where student prefixes drift and later teacher tokens become noise.

## When NOT to Use
Default single-teacher matching remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- No public code as of 2026-10-30.
- Not a replacement for BranchOPD / Flash-OPD horizon control.
