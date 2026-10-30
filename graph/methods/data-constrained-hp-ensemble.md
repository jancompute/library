---
id: method:data-constrained-hp-ensemble
type: method
title: 'Data-Constrained HP Transfer + Ensemble'
category: data-curriculum
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'unique-token epoch / repetition geometry (pricing / r shortlist)'
  reason: 'Repeated-Token Worth and Repetition-Count Selection remain the dual-active first hops'
  use_instead: method:repeated-token-worth
- when: 'open pretrain mix / Dolma-3 recipe'
  reason: 'OLMo-3 remains the open mix; this card is unique-data HP transfer plus ensembling'
  use_instead: method:olmo-3
assumptions:
- 'Unique tokens binding. Dense NTP. Fit HPs on smaller runs. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:data-constrained-hp-ensemble
recipes:
- recipe:data-constrained-hp-ensemble
claims:
- benchmark: 'FineWeb 100M unique tokens vs prior data-constrained recipes'
  metric: 'validation loss / PPL'
  value: '-0.15 nats (~14% PPL); monotonic in compute with ensembling; held at 12x compute'
  baseline: 'fixed-HP multi-epoch recipes without ensembling'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37842'
  notes: 'Does not retarget method:repeated-token-worth.'
tags:
- data-constrained
- ensemble
- active
---

# Data-Constrained HP Transfer + Ensemble

## Method Overview
This recipe treats unique-token pretrain as a joint HP-and-ensemble scaling problem. Transfer WD/LR with model size and epoch count instead of freezing them, then spend extra compute on ensembles rather than more repeats that overfit.

## When to Use
- Unique-data-constrained dense pretrain where prior epoch recipes raise loss as you add compute.

## When NOT to Use
Repeated-Token Worth / Repetition-Count Selection remain the dual-active first hops for epoch pricing / r shortlists.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:repeated-token-worth` or `method:repetition-count-selection`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- No public code as of 2026-10-30.
- 100M-token FineWeb; not a Dolma-3 mix.
