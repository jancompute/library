---
id: method:swe-ladder
type: method
title: 'SWE-Ladder'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:privileged-teacher-opsd'
  reason: 'VISTA remains gold-solution OPSD; SWE-Ladder stages privileged evidence by localize/reproduce/patch'
  use_instead: method:vista
- when: 'GitHub issue to patch / SWE harness'
  reason: 'mini-SWE-agent remains the issue-to-patch loop; SWE-Ladder is staged privileged distill'
  use_instead: method:mini-swe-agent
assumptions:
- 'Staged privileged OPSD for SWE agents. Code sekongger/SWE-Ladder.'
last_reviewed: '2026-10-27'
papers:
- paper:swe-ladder
recipes:
- recipe:swe-ladder
claims:
- benchmark: 'Qwen3-4B-Instruct SWE-bench Verified under R2E-Gym / OpenHands'
  metric: 'pass@1'
  value: 'R2E-Gym 9.6 to 16.4 vs GRPO 10.4 / full-patch OPSD 12.4; OpenHands 13.0 to 17.6; reversed order 11.4'
  baseline: 'GRPO; full-patch OPSD'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.33667'
  notes: 'Does not retarget method:vista or method:mini-swe-agent.'
tags:
- distillation
- swe
- active
---

# SWE-Ladder

## Method Overview
SWE-Ladder maps each rollout tool call to localize, reproduce, or patch, shows the frozen teacher only that stage's evidence, and distills stages in repair order while GRPO still trains the full trajectory.

## When to Use
- SWE agents that need stage-specific privileged evidence rather than the full gold patch at every step.

## When NOT to Use
Default on `task:privileged-teacher-opsd` remains `method:vista`. Issue-to-patch remains `method:mini-swe-agent`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:vista`.

## Gotchas & Failure Modes
- Not a replacement for `method:vista`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
