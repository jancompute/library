---
id: method:bac-mopd
type: method
title: BaC-MOPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains the matching default; BaC-MOPD consolidates diverged specialists back into one student'
    use_instead: method:opd
  - when: 'multi-teacher on-policy distillation as the library bake-off'
    reason: 'Open-MOPD remains the 83.4% bake-off; BaC-MOPD is a consolidation recipe when specialists drift far from the shared checkpoint'
    use_instead: method:open-mopd
  - when: 'training-free / forward-only fusion of same-base specialists'
    reason: 'Training-free OPD fuses without an update; BaC-MOPD uses merge only as the MOPD init'
    use_instead: method:training-free-opd
assumptions:
  - 'Same architecture and tokenizer as the specialists. Merge init, error-replay queries, frozen self-teacher, per-teacher then equal-across-teachers reverse-KL. Industrial six-specialist and open Qwen3-4B five-domain. Code announced, not released, as of 2026-11-25. Paper IM-MOPD numbers are not the library 83.4% bake-off.'
last_reviewed: '2026-11-25'
papers:
- paper:bac-mopd
recipes:
- recipe:bac-mopd
claims:
- benchmark: 'industrial six-specialist average-gain recovery vs IM-MOPD / merge'
  metric: 'fraction of specialist average gain recovered'
  value: '97.0% vs IM-MOPD 79.8% vs best merge 42.3%'
  baseline: 'IM-MOPD; weight merge'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.32515'
  notes: 'Student approaches each specialist in-domain and surpasses the perception specialist. Paper IM-MOPD is not the library 83.4% bake-off. Code will be released.'
- benchmark: 'open Qwen3-4B five-domain average-gain recovery vs IM-MOPD'
  metric: 'fraction of specialist average gain recovered'
  value: '95.7% after consolidation / 97.5% after refinement vs IM-MOPD 94.1%'
  baseline: 'IM-MOPD'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.32515'
  notes: 'Error replay plus balanced per-teacher then equal-across-teachers loss. Does not retarget Open-MOPD.'
tags:
- distillation
- mopd
- consolidation
- active
---

# BaC-MOPD

## Method Overview
Branch-and-Consolidate MOPD merges the student with diverged specialists as an init, distills on queries a specialist solves and the student fails, averages reverse-KL first per teacher then equally across teachers, and anchors with a frozen copy of the merged init. A later refinement stage closes remaining specialist gaps.

## When to Use
- Consolidating independently post-trained specialists that have drifted far from a shared checkpoint into one same-size student.

## When NOT to Use
Single-teacher matching remains `method:opd`. The library multi-teacher bake-off remains `method:open-mopd`. Training-free fusion remains `method:training-free-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Paper IM-MOPD / Open-MOPD numbers are not the library 83.4% bake-off. Does **not** replace Open-MOPD or OPD.

## Gotchas & Failure Modes
- Code announced, not released (`code_status: announced`).
- Merge-only is a poor final model; it only raises top-\(b\) overlap so teacher KL is usable.
- Loss must be averaged per teacher then equally across teachers; token or dataset size otherwise reallocates supervision.
