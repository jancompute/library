---
id: method:vopd
type: method
title: VOPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains the matching default; VOPD extrapolates the teacher with a verifier advantage'
    use_instead: method:opd
  - when: 'distill a reasoner with verifiable reward (OPD + RLVR ReLU gating)'
    reason: 'OPDVR is ReLU correctness gating of sampled-token OPD; VOPD is verifier-grounded teacher extrapolation'
    use_instead: method:opdvr
  - when: 'privileged same-size gold teacher OPSD'
    reason: 'VISTA remains privileged-teacher OPSD; VOPD is ordinary OPD plus a verifier, not gold-solution teacher context'
    use_instead: method:vista
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; VOPD is distillation, not the RLVR loss'
    use_instead: method:cispo
assumptions:
  - 'Qwen3-4B / 1.7B, same-size and 4B→1.7B. λ=0.25. Frozen reference plus teacher logits. Extra frozen-reference pass. Code juntongshi48/VOPD announced, not released as of 2026-11-24. Distinct from holi-lab/vOPD (2605.07865).'
last_reviewed: '2026-11-24'
papers:
- paper:vopd
recipes:
- recipe:vopd
claims:
- benchmark: 'Qwen3-4B same-size eight-bench avg vs OPD / ExOPD / teacher'
  metric: 'avg accuracy; AIME24'
  value: '66.38 vs OPD 64.71 / OPD+GRPO 64.75 / ExOPD 65.25 / teacher 64.16; AIME24 73.33 vs OPD 69.58'
  baseline: 'OPD; OPD+GRPO; ExOPD; MiniMax-M1.5 4B teacher'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.30325'
  notes: 'λ=0.25. Same-size student exceeds the RL teacher average. Distinct from OPDVR. Does not retarget OPD.'
- benchmark: 'Qwen3-4B→1.7B eight-bench avg vs OPD / ExOPD'
  metric: 'avg accuracy'
  value: '53.32 vs OPD 50.88 / ExOPD 52.34'
  baseline: 'OPD; ExOPD'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.30325'
  notes: 'Strong-to-weak still leads. Larger λ degrades. Code announced, not released.'
tags:
- distillation
- opd
- verifier
- rlvr
- active
---

# VOPD

## Method Overview
VOPD keeps reverse-KL OPD and extrapolates the teacher log-probability with a group-relative verifier advantage on student prefixes, using a frozen reference. \(\lambda=0.25\) is the reported default. Distinct from OPDVR (ReLU correctness gating of sampled-token OPD) and from holi-lab/vOPD (`arXiv:2605.07865`).

## When to Use
- Single-teacher OPD when a deterministic outcome verifier is available and the teacher target should tilt toward verified-correct prefixes.

## When NOT to Use
Matching default remains `method:opd`. ReLU correctness gating remains `method:opdvr`. Privileged gold-solution OPSD remains `method:vista`. Pass@1 RLVR remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Distinct from OPD, OPDVR, ExOPD, VISTA. Does **not** replace OPD or OPDVR.

## Gotchas & Failure Modes
- `code_status: announced` (juntongshi48/VOPD README: code will be released soon).
- Extra frozen-reference pass plus teacher logits; not a drop-in sampled-token OPD overlay.
- Do not confuse with holi-lab/vOPD (`arXiv:2605.07865`), a different control-variate KL baseline.
