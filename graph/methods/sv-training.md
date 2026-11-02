---
id: method:sv-training
type: method
title: 'SV-Training'
category: alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:instruct-sft-alignment'
  reason: 'OLMo-3 remains the open instruct stack; SV-Training is a residual-stream hook'
  use_instead: method:olmo-3
- when: 'same-tokenizer single-teacher matching distillation'
  reason: 'OPD remains matching; SV-Training injects a steering direction during teacher-forced distill'
  use_instead: method:opd
- when: 'single-turn dense math/code Pass@1 RLVR'
  reason: 'CISPO remains Pass@1; SV-Training repairs GRPO advantages on all-wrong groups'
  use_instead: method:cispo
assumptions:
- 'SFT, distillation, or GRPO with a residual-stream steering direction. Official code tiejin98/sv_training.'
last_reviewed: '2026-11-02'
papers:
- paper:sv-training
recipes:
- recipe:sv-training
claims:
- benchmark: 'SFT/distill from thinking-mode teachers; GRPO all-wrong groups'
  metric: 'accuracy vs plain SFT/distill; recovered GRPO signal'
  value: 'up to +12% thinking-teacher distill (3 seeds); advantage-repair transfers to held-out math'
  baseline: 'plain SFT/distill; GRPO without SV repair; entropy-aware zero-variance remedies'
  date: '2026-11-02'
  verified: true
  evidence_level: peer-reviewed
  source_url: 'https://arxiv.org/abs/2610.40998'
  notes: 'NeurIPS 2026. Does not retarget method:olmo-3, method:opd, or method:cispo. Mentions on task:student-distillation and task:math-code-rl-dense.'
tags:
- sft
- distillation
- rlvr
- active
---

# SV-Training

## Method Overview
SV-Training uses residual-stream steering vectors as a training signal: a hidden-state hook during teacher-forced SFT/distill, and a correctness-contrast advantage-repair on wrong GRPO rollouts including all-wrong groups.

## When to Use
- SFT or distillation with a large off-policy gap (especially thinking-mode teachers), or GRPO groups that would otherwise be zero-gradient.

## When NOT to Use
OLMo-3 remains instruct SFT. OPD remains matching distillation. CISPO remains Pass@1 RLVR.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:olmo-3`, `method:opd`, or `method:cispo`.

## Gotchas & Failure Modes
- Code generation can break the direction; cross-family layer transfer can break placement; applying the vector at inference on an SV-trained checkpoint can break the regime.
- Paper claims are NeurIPS-2026 dated 2026-11-02; no locked-SOTA bake-off.
