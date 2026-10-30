---
id: method:tace
type: method
title: 'TACE'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'single-turn dense math/code Pass@1 RLVR (one verifier reward)'
  reason: 'CISPO remains Pass@1; TACE is two-stage GRPO advantage calibration'
  use_instead: method:cispo
- when: 'Pearson / density multi-reward aggregation'
  reason: 'CorrGRPO/DARA remain the multi-reward first hop; TACE is OT+budget-neutral credit'
  use_instead: method:corrgrpo
assumptions:
- 'GRPO-style groups with a verifier scalar. Multimodal RLVR. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:tace
recipes:
- recipe:tace
claims:
- benchmark: 'multimodal RLVR GRPO vs affine group baselines'
  metric: 'reward-law shape / token-credit conservation'
  value: '1D OT to N(0,1) plus mean-1 token weights'
  baseline: 'GRPO z-score; unnormalized token confidence credit'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.40250'
  notes: 'Does not retarget method:corrgrpo or method:sapo.'
tags:
- rlvr
- credit
- active
---

# TACE

## Method Overview
TACE is a two-stage advantage estimator. First it OT-maps each task's reward law onto N(0,1) so heavy tails and binary cliffs do not leak into the gradient. Then it assigns token credit from a rank-calibrated evidence contrast and rescales so the tokens sum to the sequence signal.

## When to Use
- Multimodal or multi-reward GRPO where affine group z-scores pass through reward-law shape and token weights do not conserve credit.

## When NOT to Use
Single-reward dense Pass@1 remains CISPO. Multi-reward aggregation first hop remains CorrGRPO+DARA. MoE/VL loss remains SAPO.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:corrgrpo`, `method:dara`, or `method:sapo`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- No public code as of 2026-10-30.
