---
id: method:edit-opd
type: method
title: 'Edit-OPD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:student-distillation'
  reason: 'OPD remains token matching; Edit-OPD edits the student''s own trajectory instead of imitating a full teacher trace'
  use_instead: method:opd
assumptions:
- 'VLM math/diagram reasoning. No public code as of 2026-10-26.'
last_reviewed: '2026-10-26'
papers:
- paper:edit-opd
recipes:
- recipe:edit-opd
claims:
- benchmark: 'Multimodal visual-math reasoning vs full-trace imitation OPD'
  metric: 'recovery from perceptual misreads without full teacher imitation'
  value: 'minimal edits of the student''s own on-policy trace vs imitating a complete teacher description'
  baseline: 'full-trace OPD / SFT imitation of teacher descriptions'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.30231'
  notes: 'Does not retarget method:opd.'
tags:
- distillation
- vlm
- active
---

# Edit-OPD

## Method Overview
Edit-OPD repairs VLM perceptual failures by minimal on-policy edits instead of imitating a full teacher trace, because diagram misreads poison later reasoning.

## When to Use
- VLM math where the student misreads the diagram and full teacher imitation is the wrong target.

## When NOT to Use
Default on `task:student-distillation` remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Not a replacement for `method:opd`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
