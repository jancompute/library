---
id: method:fprt
type: method
title: 'FPRT (Failure Profiling and Reachable Trajectories)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'choosing the single-teacher distillation algorithm'
  reason: 'OPD remains matching; FPRT is SFT data construction from profiled failures'
  use_instead: method:opd
- when: 'projected distillation of failed student attempts into close correct targets'
  reason: 'Projected distillation edits failed on-policy traces; FPRT builds an SFT corpus from failure modes plus reachability'
  use_instead: method:projected-distillation
- when: 'verifiable labels exist and the goal is Pass@1 RLVR'
  reason: 'CISPO remains Pass@1; FPRT is offline SFT construction'
  use_instead: method:cispo
assumptions:
- 'SFT on constructed corrective traces. Paper: Llama-3.1-8B-Instruct / DeepSeek-Math-7B-Instruct, DeepSeek-V3.2 teacher, MetaMathQA 394.99K profiled with K=5, N=5 teacher candidates, 88.90K train. NeurIPS 2026. Code visresearch/FPRT released as of 2026-11-09. arXiv 2611.09042 above watermark 2611.08453.'
last_reviewed: '2026-11-09'
papers:
- paper:fprt
recipes:
- recipe:fprt
claims:
- benchmark: 'Llama-3.1-8B / DeepSeek-Math-7B five-bench avg at 88.90K (Table 2)'
  metric: 'avg accuracy vs LEMMA'
  value: '79.7 / 80.6 vs LEMMA +2.4 / +1.8'
  baseline: 'LEMMA / RFT / ISC / SFT / S3C-Math'
  date: '2026-11-09'
  verified: true
  evidence_level: peer-reviewed
  source_url: 'https://arxiv.org/abs/2611.09042'
  notes: 'Does not retarget method:opd. Trails LEMMA on MATH; lead is concentrated on OOD benches. Distinct from method:projected-distillation.'
tags:
- distillation
- sft
- data
- active
---

# FPRT (Failure Profiling and Reachable Trajectories)

## Method Overview
FPRT constructs an SFT corpus: profile student errors as stubborn / inconsistent / sporadic, then keep teacher corrections whose first-error branching point is reachable from the student's own traces. It is not an OPD trainer.

## When to Use
- Offline math SFT where uniform error-correction data (LEMMA-style) does not match the student's failure mode.

## When NOT to Use
Live matching remains `method:opd`. Near-on-policy repair of failed rollouts remains `method:projected-distillation`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Distinct from `method:projected-distillation`. Does **not** replace OPD.

## Gotchas & Failure Modes
- Trails LEMMA on MATH; do not pick FPRT when MATH is the only score that matters.
- Branching-point audit is 88% on a 50-trace sample; boundary noise of 12% moved avg $80.0\to 79.7$ in one run.
