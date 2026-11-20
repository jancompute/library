---
id: method:visalloc
type: method
title: VisAlloc
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'privileged-teacher OPSD for text math with gold solutions (VISTA bake-off)'
    reason: 'VISTA remains text-math privileged-OPSD SOTA; VisAlloc is MLLM crop-filter OPSD'
    use_instead: method:vista
  - when: 'MLLM privileged OPSD with textual spatial guidance from synthetic scenes (not crop-zoom teachers)'
    reason: 'Where-OPD is textual object/coord hints; VisAlloc uses geometry-matched crops'
    use_instead: method:where-opd
  - when: 'contrastive vision OPD for VLMs (positive/negative crops, visual-token gate)'
    reason: 'CV-OPD is contrastive crop OPD; VisAlloc is privileged OPSD with a conserved token budget'
    use_instead: method:cv-opd
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains matching; VisAlloc is MLLM privileged OPSD'
    use_instead: method:opd
assumptions:
  - 'Qwen3.5-4B/9B. 96 prompts/batch, 8 rollouts, lr 2e-6, EMA 0.05, 1024-token responses. Vision-OPD is not a library node. Code Kaelyn01/VisAlloc as of 2026-11-20.'
last_reviewed: '2026-11-20'
papers:
- paper:visalloc
recipes:
- recipe:visalloc
claims:
- benchmark: 'Qwen3.5-4B/9B eight-bench macro vs Vision-OPD reproduction'
  metric: 'macro accuracy'
  value: '4B 81.44 vs 80.47 (+0.97); 9B 84.92 vs 84.40 (+0.52); 9B vs OPD-V +1.56'
  baseline: 'Vision-OPD (Yuan et al. 2605.18740, reproduced); OPD-V'
  date: '2026-11-20'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.25069'
  notes: 'Single-seed. Trails MMVP/POPE at 4B. Does not retarget method:vista / method:where-opd / method:cv-opd.'
tags:
- opsd
- mllm
- visalloc
- privileged-teacher
- active
---

# VisAlloc

## Method Overview
VisAlloc filters OPSD samples with a frozen paired teacher (evidence crop vs displaced crop) then reweights student tokens by view sensitivity and teacher–teacher JSD. Inverse-frequency redistribution keeps extra weight conserved inside each micro-batch. Only the positive teacher is distilled; inference is full-image.

## When to Use
- MLLM privileged OPSD when you can build geometry-matched crops and want to drop samples the negative view already solves.

## When NOT to Use
Text-math gold OPSD remains `method:vista`. Textual spatial hints remain `method:where-opd`. Contrastive crop matching remains `method:cv-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:privileged-teacher-opsd`. Mention on `task:student-distillation`. Vision-OPD is not a library node. Does **not** replace VISTA.

## Gotchas & Failure Modes
- Eight-task macro equally weights benches of different size; report per-bench scores.
- 4B trails Vision-OPD on MMVP and POPE.
- Single-seed 4B/9B; 9B gain (0.52) is smaller than 4B (0.97).
