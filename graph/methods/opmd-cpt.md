---
id: method:opmd-cpt
type: method
title: 'OPMD (On-Policy Mid-Training Distillation)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
    - when: 'same-tokenizer single-teacher matching distillation'
      reason: 'OPD remains post-train matching; this OPMD is continual-pretrain / mid-training reverse-KL'
      use_instead: method:opd
    - when: 'on-policy mechanism distillation beyond output supervision (existing OPMD)'
      reason: 'method:opmd (2610.14022) is post-train mechanism compatibility; this card is mid-training CPT'
      use_instead: method:opmd
    - when: 'one-step prefix-augmented OPD for continued pretrain'
      reason: 'PA1-OPD is output-space prefix OPD on ground-truth prefixes; OPMD-CPT rollouts from corpus anchors'
      use_instead: method:pa1-opd
assumptions:
    - 'Frozen teacher, student rollouts from high-entropy corpus anchors, reverse-KL on student tokens. Distinct from method:opmd (arXiv 2610.14022). GitHub ShuidiH20/OPMD 404 as of 2026-11-11. Paper: Qwen3-1.7B-Base, 1B MegaMath-Web-Pro tokens. arXiv 2611.13855 above watermark 2611.12886.'
last_reviewed: '2026-11-11'
papers:
- paper:opmd-cpt
recipes:
- recipe:opmd-cpt
claims:
- benchmark: 'Qwen3-1.7B-Base MATH-500 / Minerva after 1B MegaMath tokens'
  metric: 'pass@16 vs NTP CPT'
  value: 'MATH-500 76.6→82.8 vs NTP 76.6→18.2; Minerva 30.5→34.9/36.0 vs NTP 30.5→5.5'
  baseline: 'NTP continued pretrain on the same 1B-token stream (catastrophic collapse on Qwen)'
  date: '2026-11-11'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.13855'
  notes: 'Does not retarget method:opd or method:opmd. Llama-3.2-3B NTP on the same corpus improves; Qwen NTP collapses. 4B vs 14B teachers are comparable. GitHub ShuidiH20/OPMD 404 (code_status: announced).'
tags:
- distillation
- continued-pretrain
- mid-training
- opd
- active
---

# OPMD (On-Policy Mid-Training Distillation)

## Method Overview
OPMD-CPT turns continual pretrain into query-driven reverse-KL OPD. A proxy marks high-entropy corpus anchors, the student rollouts from those prefixes, and a frozen teacher provides dense token-level reverse-KL on the student's own states. NTP on the same 1B MegaMath tokens collapses Qwen3-1.7B-Base MATH-500 pass@16 from $76.6$ to $18.2$; OPMD-CPT raises it to $82.8$. Distinct from `method:opmd` (post-train mechanism OPD, `arXiv:2610.14022`).

## When to Use
- Domain mid-training / CPT of a strong reasoner checkpoint where teacher-forced NTP would overwrite post-train skills.

## When NOT to Use
Output matching remains `method:opd`. Post-train mechanism OPD remains `method:opmd`. Prefix-augmented OPD for CPT remains `method:pa1-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Mention on `task:pretrain-dense-7b`. Does **not** replace OPD or the existing OPMD card.

## Gotchas & Failure Modes
- GitHub ShuidiH20/OPMD 404 (`code_status: announced`).
- Distinct from `method:opmd` / `paper:opmd` (`arXiv:2610.14022`); do not merge the cards.
- NTP on the same corpus helps Llama-3.2-3B and hurts Qwen3-1.7B-Base — the failure is model-dependent.
