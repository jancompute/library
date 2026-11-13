---
id: method:sparse-teacher-support
type: method
title: Sparse Teacher Support
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains reverse-KL matching; this card is a forward-KL vocab-support cut on stored teacher scores'
    use_instead: method:opd
  - when: 'sparse OPD token budget (1–2 tokens per trajectory)'
    reason: 'Sparse OPD drops student tokens under reverse-KL; Sparse Teacher Support drops teacher vocab mass under forward-KL'
    use_instead: method:sparse-opd-supervision
  - when: 'ordinal top-K OPD without probability values (O3PD)'
    reason: 'O3PD is reverse-KL rank matching; this card renormalizes a top-mass teacher slice for forward-KL'
    use_instead: method:order-only-opd
assumptions:
  - 'Forward-KL reasoning distill with cached teacher scores. Main study Qwen3 4B→1.7B. No public trainer as of 2026-11-13.'
last_reviewed: '2026-11-13'
papers:
- paper:sparse-teacher-support
recipes:
- recipe:sparse-teacher-support
claims:
- benchmark: 'Qwen3 4B→1.7B MMLU-Pro; step time with cached teacher scores; peak mem; Nemotron Nano support floor'
  metric: 'MMLU-Pro vs full-vocab FKL; step-time cut; peak mem cut; minimum support that keeps the closing reasoning tag'
  value: '0.01% vocab (k=15 of 151936) no MMLU-Pro drop; 38% step-time cut; 24% peak mem; Nemotron Nano matches at 0.1%, smaller fractions fail the closing tag'
  baseline: 'full-vocab forward-KL'
  date: '2026-11-13'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.14850'
  notes: 'Does not retarget method:opd. Distinct from method:sparse-opd-supervision and method:order-only-opd. No public code.'
tags:
- distillation
- forward-kl
- sparse-vocab
- active
---

# Sparse Teacher Support

## Method Overview
Sparse Teacher Support is forward-KL distillation on a renormalized slice of the teacher's highest-probability vocabulary. The student never scores the dropped tail. Cached teacher scores plus a compact student output cut step time 38% and peak memory 24% on Qwen3 4B→1.7B, with no MMLU-Pro drop at 0.01% vocab ($k=15$ of 151936).

## When to Use
- Forward-KL reasoning distill where full-vocab teacher scores dominate step time or stored targets.

## When NOT to Use
Reverse-KL matching remains `method:opd`. Reverse-KL token keep-masks remain `method:sparse-opd-supervision`. Ordinal top-K without probabilities remains `method:order-only-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Does **not** replace OPD.

## Gotchas & Failure Modes
- Nemotron Nano fails the closing reasoning tag below 0.1% support even when MMLU-Pro looks intact.
- This is not a reverse-KL OPD token budget.
- No public trainer as of 2026-11-13.
