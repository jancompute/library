---
id: method:concertina
type: method
title: Concertina
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains reverse-KL matching on student rollouts; Concertina folds teacher layers into a looped student then FKL+CE distills'
    use_instead: method:opd
  - when: 'elastic mixed-depth looped LM (gated state update / mixed loop counts)'
    reason: 'ELR remains mixed-depth elastic recurrence from scratch; Concertina folds an existing teacher'
    use_instead: method:elr
assumptions:
  - 'Start from a finished teacher (paper: Qwen3-4B). Fold every N adjacent layers into one shared block executed N times. Mix 35% math / 55% knowledge / 10% web. Code released at myboker/concertina as of 2026-11-16.'
last_reviewed: '2026-11-16'
papers:
- paper:concertina
recipes:
- recipe:concertina
claims:
- benchmark: 'Qwen3-4B folded N=2 → 2.27B (57% params) on 22B tokens; base-7 / GSM8K / MATH / 8-task avg vs teacher'
  metric: 'student / teacher accuracy'
  value: 'base-7 92%, GSM8K 90%, MATH 88%, 84% avg of teacher; beats Qwen3-1.7B (36T tokens) on 6/8; vs same-size dense student +8–11 MMLU family / ~41× GSM8K'
  baseline: 'Qwen3-4B teacher; Qwen3-1.7B 36T; same-size dense student'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.18113'
  notes: 'Does not retarget method:opd. Mention on task:elastic-depth-looped-lm. SVD-init low-rank step corrections plus a per-token gate.'
tags:
- distillation
- looped-lm
- folding
- active
---

# Concertina

## Method Overview
Concertina builds the student from the teacher's weights. Every group of N adjacent teacher layers is folded into one shared block that runs N times. Each loop step carries a low-rank correction initialized from the layer it replaces, plus a per-token gate. Training is forward-KL plus CE on a 35/55/10 math/knowledge/web mix, not reverse-KL OPD on student rollouts.

## When to Use
- Compress a finished dense teacher into a looped student when the teacher's weights already encode most of what the student needs.

## When NOT to Use
Single-teacher matching remains `method:opd`. Mixed-depth elastic pretrain remains `method:elr`. Residual looped pretrain from scratch remains `method:loopback-transformer`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Mention on `task:elastic-depth-looped-lm`. Does **not** replace OPD.

## Gotchas & Failure Modes
- FKL+CE on folded weights is not reverse-KL OPD; do not swap the loss family.
- Paper mix is 35% math, 55% knowledge, 10% web; N=2 is the reported 4B→2.27B setting.
- Code: `https://github.com/myboker/concertina` (`code_status: released`).
