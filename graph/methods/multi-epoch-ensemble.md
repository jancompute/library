---
id: method:multi-epoch-ensemble
type: method
title: 'Multi-Epoch Ensemble'
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:data-constrained-pretrain'
  reason: 'Repeated-Token Worth remains unique-token epoch pricing; this is late-time logit ensembling'
  use_instead: method:repeated-token-worth
assumptions:
- 'FineWeb unique-token budget. Complementary to Repeated-Token Worth. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:multi-epoch-ensemble
recipes:
- recipe:multi-epoch-ensemble
claims:
- benchmark: 'FineWeb multi-epoch pretrain at fixed unique tokens'
  metric: 'late-time test error / matched parameter-token vs wider/deeper singles'
  value: 'logit averaging reduces late-training deterioration and can beat wider or deeper singles'
  baseline: 'single-model multi-epoch SGD without ensembling'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03590'
  notes: 'Does not retarget method:repeated-token-worth.'
tags:
- pretrain
- ensemble
- data-constrained
- active
---

# Multi-Epoch Ensemble

## Method Overview
When data are fixed, train several multi-epoch members and average logits; the paper's DMFT says to grow ensemble size at least as fast as steps per member.

## When to Use
- Data-constrained pretrain where a second epoch helps but late-time error grows, and you can afford several members.

## When NOT to Use
Repeated-Token Worth remains the dual-active first hop. OLMo-3 remains the open mix.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:repeated-token-worth`.

## Gotchas & Failure Modes
- Ensemble, not a new optimizer.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
