---
id: method:recurrent-student-opd
type: method
title: Recurrent Student OPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains the matching default; this node converts the student to recurrence during OPD'
    use_instead: method:opd
  - when: 'elastic mixed-depth looped LM (gated state update / mixed loop counts)'
    reason: 'ELR is mixed-depth looping from pretrain; this node is post-train student recurrence during OPD'
    use_instead: method:elr
  - when: 'fold N teacher layers into a shared loop then FKL+CE (Concertina; not mixed-depth ELR)'
    reason: 'Concertina folds teacher layers; this node adds student recurrence'
    use_instead: method:concertina
  - when: 'residual looped pretrain / Loopback Transformer (not mixed-depth ELR)'
    reason: 'Loopback is residual looped pretrain, not student OPD recurrence'
    use_instead: method:loopback-transformer
  - when: 'recurrent CED-style architecture / all-token recurrence'
    reason: 'RLT is experimental CED; this node is cross-token student recurrence during OPD'
    use_instead: method:recurrent-looped-transformer
assumptions:
  - 'From-scratch 0.4B + 3.9B teacher OPD; pretrained Qwen2.5-0.5B + 3B/7B teachers. Recurrence ~+3% params, 1.1× decode, vanilla KV. Loop 3 is an intermediate. No public code as of 2026-11-24.'
last_reviewed: '2026-11-24'
papers:
- paper:recurrent-student-opd
recipes:
- recipe:recurrent-student-opd
claims:
- benchmark: 'From-scratch 0.4B student + 3.9B teacher OPD, recurrent vs vanilla'
  metric: 'GSM8K / MATH500'
  value: '47.2 / 34.2 vs vanilla OPD 36.7 / 28.2 (+10.7 / +6.0)'
  baseline: 'vanilla OPD student; TF-KD pretrain'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.28603'
  notes: 'Recurrent student keeps improving as teacher size grows; vanilla OPD plateaus. No public GitHub.'
- benchmark: 'Pretrained Qwen2.5-0.5B + 7B teacher OPD, recurrent vs vanilla'
  metric: 'GSM8K / MATH500'
  value: '57.5 / 41.6 vs vanilla OPD 53.7 / 37.6; 3B teacher 56.5 / 41.2 vs 52.2 / 38.6'
  baseline: 'vanilla OPD on the same pretrained student'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.28603'
  notes: 'Joint architecture conversion + OPD; no repeated pretrain. Loop 3 sits between vanilla and recurrence. Does not retarget ELR or OPD.'
tags:
- distillation
- opd
- recurrence
- architecture
- active
---

# Recurrent Student OPD

## Method Overview
Convert the student into cross-token recurrence (or Loop 3) in the same OPD fine-tune. Recurrence adds ~3% parameters and \(1.1\times\) decode latency with a vanilla KV cache. Joint conversion plus OPD from a pretrained Qwen2.5-0.5B avoids repeating pretrain. Distinct from ELR mixed-depth looping and Concertina teacher-layer folding.

## When to Use
- Distilling a larger teacher into a small student when vanilla OPD plateaus as teacher size grows.

## When NOT to Use
Matching default remains `method:opd`. Mixed-depth looping remains `method:elr`. Teacher-layer folding remains `method:concertina`. Residual looped pretrain remains `method:loopback-transformer`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Mention on `task:elastic-depth-looped-lm`. Distinct from ELR, Concertina, Loopback, RLT. Does **not** replace OPD or ELR.

## Gotchas & Failure Modes
- No public code at ingest (`code_status: none`).
- Recurrence is a student architecture change, not a loss-only overlay.
- Post-train looping on a finished checkpoint has a no-free-loop warning (`paper:no-free-loop`); this node jointly converts during OPD, not after freeze.
