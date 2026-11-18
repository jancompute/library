---
id: method:m3opd-reasoner
type: method
title: M3OPD-Reasoner
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the multi-teacher distillation algorithm'
    reason: 'Open-MOPD remains text token-share / gap-aware budget; M3OPD-Reasoner is VLM GSPO teachers then MOPD then MixRL'
    use_instead: method:open-mopd
  - when: 'observation-aligned MOPD for VL agents (Reframe)'
    reason: 'Reframe mixes teachers at the shared observation; M3OPD-Reasoner is domain GSPO teachers then MOPD then MixRL'
    use_instead: method:reframe
  - when: 'choosing the single-teacher distillation algorithm'
    reason: 'OPD remains matching; M3OPD-Reasoner is a VLM multi-teacher then MixRL recipe'
    use_instead: method:opd
  - when: 'OPD-then-RLVR stacking order on text'
    reason: 'opd-then-rlvr is text stacking; M3OPD-Reasoner is the VLM analog with GSPO teachers'
    use_instead: method:opd-then-rlvr
assumptions:
  - 'Qwen3.5-9B VLM with labeled image-STEM / image-perception / video prompts. Paper MOPD is not the library 83.4% bake-off. Code ngquangtrung57/M3OPD-Reasoner released as of 2026-11-18.'
last_reviewed: '2026-11-18'
papers:
- paper:m3opd-reasoner
recipes:
- recipe:m3opd-reasoner
claims:
- benchmark: 'Qwen3.5-9B 21-bench avg@8 (STEM / perception / video / overall)'
  metric: 'avg@8 accuracy'
  value: 'MOPD+MixRL 77.1 / 81.9 / 64.1 / 75.9 vs MixRL 74.9 / 80.8 / 63.4 / 74.4; GSPO teachers dagger overall 75.2'
  baseline: 'MixRL from Qwen3.5-9B; GSPO domain teachers'
  date: '2026-11-18'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.23034'
  notes: 'Does not retarget method:open-mopd or method:reframe. Paper MOPD is not the library 83.4% bake-off. Code ngquangtrung57/M3OPD-Reasoner.'
tags:
- distillation
- mopd
- vision
- gspo
- active
---

# M3OPD-Reasoner

## Method Overview
M3OPD-Reasoner trains one GSPO teacher per VLM domain from Qwen3.5-9B, distills them into one student with top-32 reverse-KL MOPD, then continues MixRL on the same 193K prompts. The MixRL stage still improves the MOPD student with no collapse.

## When to Use
- VLM post-train when you can train domain GSPO teachers and then merge them with MOPD before mixed RL.

## When NOT to Use
Text multi-teacher default remains `method:open-mopd`. Observation-aligned VL mix remains `method:reframe`. Single-teacher matching remains `method:opd`. Text OPD-then-RLVR remains `method:opd-then-rlvr`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Does **not** replace Open-MOPD or Reframe.

## Gotchas & Failure Modes
- Paper MOPD numbers are not the library 83.4% bake-off.
- SFT warm-up before GSPO teachers is worse than GSPO from the base in this recipe.
- Distinct slug from `method:reframe` and `method:open-mopd`.
