---
id: method:muon-rt
type: method
title: 'Muon-RT'
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:llm-pretraining-optimization'
  reason: 'Muon2 remains the ~7B optimizer; Muon-RT reuses an EMA teacher trajectory for self-distillation'
  use_instead: method:muon2
- when: 'same-tokenizer single-teacher matching distillation'
  reason: 'OPD remains matching; Muon-RT is a Muon-family optimizer for EMA self-distillation'
  use_instead: method:opd
assumptions:
- 'EMA-teacher self-distillation (SDFT / SDPO). No public code as of 2026-11-02.'
last_reviewed: '2026-11-02'
papers:
- paper:muon-rt
recipes:
- recipe:muon-rt
claims:
- benchmark: 'Qwen2.5-7B-Instruct SDFT; Olmo-3-7B-Instruct SDPO'
  metric: 'average accuracy vs AdamW / momentum Muon; persistent optimizer memory'
  value: 'SDFT +2.6 vs AdamW (42% less mem) / +5.4 vs momentum Muon (27% less); SDPO +2.0 vs AdamW'
  baseline: 'AdamW; momentum Muon'
  date: '2026-11-02'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.41104'
  notes: 'Does not retarget method:muon2. Mention on task:student-distillation.'
tags:
- muon
- distillation
- active
---

# Muon-RT

## Method Overview
Muon-RT drops Muon momentum on hidden matrices and reuses the EMA teacher-student displacement as the history: remove the radial component, spectrally normalize, then mix with the Newton-Schulz orthogonalized gradient.

## When to Use
- Self-distillation with an EMA teacher where Muon momentum is extra persistent memory.

## When NOT to Use
Muon2 remains the ~7B pretrain optimizer. OPD remains matching distillation.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:muon2` or `method:opd`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-11-02; no locked-SOTA bake-off.
- Requires an EMA teacher; not a drop-in for from-scratch NTP.
- No public code as of 2026-11-02.
