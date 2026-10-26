---
id: method:drive-ft
type: method
title: 'DRIVE'
category: data-curriculum
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:instruct-sft-alignment'
  reason: 'OLMo-3 remains the open instruct stack; DRIVE reweights inaccessible-source SFT to limit forgetting'
  use_instead: method:olmo-3
assumptions:
- 'Single-stage FT without source pretrain data. Code luciabcd/DRIVE.'
last_reviewed: '2026-10-26'
papers:
- paper:drive-ft
recipes:
- recipe:drive-ft
claims:
- benchmark: 'Single-stage FT forgetting vs uniform SFT / contribution-only weights'
  metric: 'retention of source behavior vs new-task adaptation'
  value: 'contribution- and diversity-aware sample weights plus a prior regularizer when source data is gone'
  baseline: 'uniform SFT; contribution-only weighting'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32501'
  notes: 'Does not retarget method:olmo-3.'
tags:
- sft
- forgetting
- active
---

# DRIVE

## Method Overview
DRIVE weights SFT examples by contribution and diversity and adds a prior regularizer so single-stage FT forgets less when the pretrain corpus is inaccessible.

## When to Use
- Instruct FT where you cannot mix source data back in and uniform SFT overwrites it.

## When NOT to Use
Default on `task:instruct-sft-alignment` remains `method:olmo-3`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:olmo-3`.

## Gotchas & Failure Modes
- Not a replacement for `method:olmo-3`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
