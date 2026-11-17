---
id: method:ta-opsd
type: method
title: TA-OPSD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'privileged-teacher math OPSD with gold solutions (VISTA default)'
    reason: 'VISTA remains the first hop; TA-OPSD adds stop/continue distill plus repetition unlikelihood on OPSD'
    use_instead: method:vista
  - when: 'OPD EOS termination / teacher-student stop-id mismatch'
    reason: 'opd-eos is a stop-id / semantic-class patch on OPD; TA-OPSD is premature-stop vs repetition on privileged OPSD'
    use_instead: method:opd-eos
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains matching; TA-OPSD is privileged OPSD termination'
    use_instead: method:opd
assumptions:
  - 'Privileged OPSD on Qwen3 1.7B/4B/8B math. Teacher-student EOS discrepancy grows during vanilla OPSD; length-capped traces are often unproductive repetition. Code gtbxdf4/TA-OPSD.'
last_reviewed: '2026-11-17'
papers:
- paper:ta-opsd
recipes:
- recipe:ta-opsd
claims:
- benchmark: 'Qwen3 1.7B/4B/8B mathematical reasoning vs OPSD'
  metric: 'accuracy; premature termination; repetition-driven over-generation'
  value: 'consistently outperforms OPSD and other baselines at all three scales; Stop/Continue Distillation cuts premature stop; Repetition-Aware Unlikelihood cuts stalled repetition'
  baseline: 'vanilla OPSD (gold-conditioned frozen teacher)'
  date: '2026-11-17'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.19925'
  notes: 'Does not retarget method:vista / method:opd / method:opd-eos. Distinct from method:opd-eos (stop-id mismatch).'
tags:
- opsd
- termination
- privileged-teacher
- active
---

# TA-OPSD

## Method Overview
TA-OPSD (Termination-Aware On-Policy Self-Distillation) keeps the OPSD student update and adds two losses. Stop/Continue Distillation aligns teacher and student on whether reasoning should continue (premature EOS). Repetition-Aware Unlikelihood Training downweights repetitive continuations on the student's failed traces (over-generation).

## When to Use
- Privileged OPSD when the student stops too early or loops after reasoning stalls.

## When NOT to Use
Gold-solution OPSD default remains `method:vista`. Stop-id mismatch on OPD remains `method:opd-eos`. Student matching remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:privileged-teacher-opsd`. Does **not** replace VISTA or OPD.

## Gotchas & Failure Modes
- Teacher-student EOS discrepancy grows under vanilla OPSD; do not treat that as an OPD stop-id bug (`method:opd-eos`).
