---
id: method:gift
type: method
title: 'GIFT'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:student-distillation'
  reason: 'OPD remains matching; GIFT keeps distillation tokens whose gradient agrees with the RL objective'
  use_instead: method:opd
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'GIFT is a distill+RL token filter; method:cispo remains Pass@1'
  use_instead: method:cispo
assumptions:
- 'Distillation-augmented reasoning RL. Code lilifree/GIFT.'
last_reviewed: '2026-10-26'
papers:
- paper:gift
recipes:
- recipe:gift
claims:
- benchmark: 'Distillation-augmented reasoning RL vs unfiltered distill+RL'
  metric: 'compatibility of token-level distill grads with the outcome RL objective'
  value: 'filters imitation tokens that conflict with outcome RL; complementarity of signals is not compatibility of grads'
  baseline: 'unfiltered distillation-augmented RL / OPD-style matching'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.30796'
  notes: 'Does not retarget method:opd.'
tags:
- distillation
- rlvr
- active
---

# GIFT

## Method Overview
GIFT keeps distillation tokens whose gradient agrees with the RL objective so imitation-focused distill does not fight outcome-driven RL.

## When to Use
- Reasoning RL that mixes sparse outcome reward with dense teacher distillation and the two grads conflict.

## When NOT to Use
Default on `task:student-distillation` remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd`.

## Gotchas & Failure Modes
- Not a replacement for `method:opd`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
