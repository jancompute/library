---
id: method:bernoulli-opd
type: method
title: 'Bernoulli OPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'same-tokenizer single-teacher matching distillation'
  reason: 'OPD remains matching; Bernoulli OPD is a probability-space token match'
  use_instead: method:opd
assumptions:
- 'Sampled-token OPD. Official code duterscmy/Bernoulli-OPD.'
last_reviewed: '2026-11-03'
papers:
- paper:bernoulli-opd
recipes:
- recipe:bernoulli-opd
claims:
- benchmark: 'fixed-rollout OPD analyses; reasoning students'
  metric: 'high-confidence token gradient mass / student quality'
  value: 'restores signal to high-confidence tokens vs sampled reverse-KL OPD'
  baseline: 'sampled reverse-KL OPD'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.02093'
  notes: 'Code duterscmy/Bernoulli-OPD. Does not retarget method:opd.'
tags:
- opd
- token-matching
- active
---

# Bernoulli OPD

## Method Overview
Bernoulli OPD replaces reverse-KL token matching with a Bernoulli probability match on the sampled token so high-confidence student tokens still receive teacher disagreement.

## When to Use
- Sampled-token reverse-KL OPD where high-confidence student tokens stop moving.

## When NOT to Use
OPD remains the matching default.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Gains are not explained by longer reasoning or larger steps in the paper.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
