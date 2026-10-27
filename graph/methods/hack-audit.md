---
id: method:hack-audit
type: method
title: 'Hack-Audit (LB)'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:math-code-rl-dense'
  reason: 'CISPO remains Pass@1; LB spends a strong-verifier budget on low-pass GRPO groups'
  use_instead: method:cispo
assumptions:
- 'Budgeted strong-verifier audits on GRPO. No public code as of 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:hack-audit
recipes:
- recipe:hack-audit
claims:
- benchmark: 'LeetCode / Countdown-Code GRPO hacking vs random audits'
  metric: 'hack rate at fixed strong-verifier budget'
  value: 'LB drives hacking near zero; same-budget random audits do not; 33/39 runs including 13/16 preregistered match the frozen-panel sign'
  baseline: 'random strong-verifier audits; unaudited weak unit tests'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.35716'
  notes: 'Does not retarget method:cispo.'
tags:
- rl-alignment
- active
---

# Hack-Audit (LB)

## Method Overview
Hack-Audit audits whole GRPO groups with the fewest weak passes first and reflects a caught hack about the failure reward so an all-hack group does not keep a positive advantage.

## When to Use
- GRPO-family code RL on cheap unit tests when a strong verifier can only score a budgeted subset.

## When NOT to Use
Default on `task:math-code-rl-dense` remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:cispo`.

## Gotchas & Failure Modes
- Not a replacement for `method:cispo`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
