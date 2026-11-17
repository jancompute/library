---
id: method:specal
type: method
title: SpeCal
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'unlabeled existing math problems with majority-vote pseudo-solutions'
    reason: 'u-OPSD remains the unlabeled first hop; SpeCal calibrates unsupervised RLVR advantages from hidden-state spectra'
    use_instead: method:u-opsd
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; SpeCal is a spectral gate on unlabeled RLVR'
    use_instead: method:cispo
  - when: 'majority-vote unsupervised RLVR collapse from cross-task coupling'
    reason: 'Gotcha on unlabeled RLVR coupling; SpeCal is a spectral calibrator, not that collapse fix'
    use_instead: paper:unsupervised-rlvr-collapse
assumptions:
  - 'Unsupervised RLVR with a self-generated scalar reward already in place. SpeCal rescales group and rollout advantages from hidden-state spectra; it does not redefine the unlabeled reward. KDD 2027. No public code as of 2026-11-17.'
last_reviewed: '2026-11-17'
papers:
- paper:specal
recipes:
- recipe:specal
claims:
- benchmark: 'Unsupervised RLVR; group-level spectral mass plus Gaussian band-pass on entropy-based effective rank; rollout-level leave-one-out spectral support'
  metric: 'advantage calibration without changing the unlabeled reward'
  value: 'bi-level spectral calibration of group and rollout advantages from hidden-state spectra rather than decoded outcomes only'
  baseline: 'unsupervised RLVR with outcome/reward-statistic gates only'
  date: '2026-11-17'
  verified: true
  evidence_level: peer-reviewed
  source_url: 'https://arxiv.org/abs/2611.20691'
  notes: 'KDD 2027. Does not retarget method:u-opsd / method:cispo. No public code.'
tags:
- rlvr
- unsupervised
- spectral
- active
---

# SpeCal

## Method Overview
SpeCal is bi-level spectral calibration for unsupervised RLVR. At the group level it combines spectral mass with a Gaussian band-pass on normalized entropy-based effective rank, keeping groups with substantial representation variation in a preferred dimensionality. At the rollout level the same effective rank sets how many dominant directions to keep in a leave-one-out spectral subspace, then measures each held-out rollout's conditional support. Those signals rescale the original reward-induced advantages; they do not replace the unlabeled reward.

## When to Use
- Unsupervised RLVR when outcome-only group/rollout gates look noisy and you can read hidden-state spectra.

## When NOT to Use
Unlabeled OPSD default remains `method:u-opsd`. Labeled Pass@1 remains `method:cispo`. Coupling collapse remains `paper:unsupervised-rlvr-collapse`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:label-free-reasoner-posttrain`. Does **not** replace u-OPSD.

## Gotchas & Failure Modes
- Does not invent a new unlabeled reward; bad endpoint rewards stay bad.
- No public trainer as of 2026-11-17 (`code_status: none`).
