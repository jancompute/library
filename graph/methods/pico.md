---
id: method:pico
type: method
title: 'PICO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:all-zero-verifier-groups'
  reason: 'VeriGate remains the all-zero / process-supervision gate; PICO jointly decodes expert-guided policy-compatible traces when groups are silent'
  use_instead: method:verigate
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; PICO is silent-group joint decoding, not the CISPO loss'
  use_instead: method:cispo
- when: 'hindsight-to-foresight distillation when verifier groups are silent (SRD)'
  reason: 'SRD distills hindsight; PICO jointly decodes expert-guided on-policy traces'
  use_instead: method:srd
assumptions:
- 'Hard-problem RLVR with expert traces used as decoding constraints, not cloned SFT. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:pico
recipes:
- recipe:pico
claims:
- benchmark: 'Reasoning datasets and agentic benches vs RLVR and off-policy expert cloning'
  metric: 'accuracy when all on-policy rollouts fail'
  value: 'consistently outperforms standard RLVR and prior off-policy baselines by decoding verifiable, policy-compatible traces'
  baseline: 'GRPO/RLOO all-fail collapse; expert-trajectory off-policy updates'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36849'
  notes: 'Does not retarget method:verigate.'
tags:
- rl-alignment
- rlvr
- all-fail
- active
---

# PICO

## Method Overview
PICO jointly decodes under a finite divergence budget: expert data guides tokens while student relative probabilities are kept, then mixed-behavior IS trains on those verified traces together with on-policy rollouts.

## When to Use
- RLVR groups that are all-fail, expert traces exist, and cloning those traces would sit in the student's low-probability region.

## When NOT to Use
Default on `task:all-zero-verifier-groups` remains `method:verigate`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:verigate`.

## Gotchas & Failure Modes
- Not a replacement for `method:verigate`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
