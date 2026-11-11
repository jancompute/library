---
id: method:lcs-opd
type: method
title: 'LCS-OPD (Action-Sequence Alignment)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
    - when: 'outcome-only AppWorld coverage / anti-drift'
      reason: 'CANOPY remains the checker-coverage first hop; LCS-OPD selects references for multi-turn OPD'
      use_instead: method:canopy
    - when: 'same-tokenizer single-teacher matching distillation'
      reason: 'OPD remains matching; LCS-OPD is a failure-only reference selector'
      use_instead: method:opd
    - when: 'state-grounded multi-turn agent OPD (matched interaction state)'
      reason: 'State-OPD matches teacher targets on student states; LCS-OPD picks which success to condition on'
      use_instead: method:state-opd
assumptions:
    - 'Multi-turn tool-use with a pool of reward-validated successes per task. Failure-only OPD. No public trainer as of 2026-11-11. arXiv 2611.13135 above watermark 2611.12886.'
last_reviewed: '2026-11-11'
papers:
- paper:lcs-opd
recipes:
- recipe:lcs-opd
claims:
- benchmark: 'ALFWorld Valid Unseen / τ³-bench airline Pass^4'
  metric: 'success vs vanilla OPD'
  value: 'ALFWorld Unseen Qwen2.5-3B 78.4→85.8 / 7B 83.6→94.0; airline Pass^4 Qwen3.5-2B 30.0→41.7 / 4B 26.7→38.3'
  baseline: 'vanilla OPD / LCP / BM25 / random / shortest / edit-distance selectors'
  date: '2026-11-11'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.13135'
  notes: 'LCS was the only selector to beat vanilla OPD on every aggregate for both students. Distilling successful rollouts hurts. Does not retarget method:canopy or method:opd.'
tags:
- distillation
- opd
- agents
- reference-selection
- active
---

# LCS-OPD (Action-Sequence Alignment)

## Method Overview
LCS-OPD treats reference selection for multi-turn OPD as free-target optimal transport and assigns each failed student trajectory the same-task success with the longest common action subsequence. Prefix matching (LCP) throws away agreement after the first unmatched action. Updates run only on failed rollouts.

## When to Use
- Multi-turn tool-use OPD where a task has several successful traces and a random or shortest reference can make the teacher worse.

## When NOT to Use
AppWorld coverage remains `method:canopy`. Text matching remains `method:opd`. Matched-state agent OPD remains `method:state-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:outcome-only-long-horizon-agent-rl`. Mention on `task:student-distillation`. Does **not** replace CANOPY or OPD.

## Gotchas & Failure Modes
- No public trainer (`code_status: none`).
- Applying OPD to already-successful rollouts drops ALFWorld and $\tau^3$ metrics.
- Observation overlap is a bad proxy; compare executed actions.
