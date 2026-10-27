---
id: method:mirl
type: method
title: 'MiRL'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:coding-agent-rl-environment-construction'
  reason: 'CodeMidas remains the source-code env factory; MiRL is error-targeted RL on terminal-agent failures'
  use_instead: method:codemidas
- when: "fork RL rollouts from the agent's own failure states (ReTerm)"
  reason: 'ReTerm forks from failure states; MiRL targets named misbehaviors then re-checks them'
  use_instead: method:reterm
assumptions:
- 'Terminal-agent error-targeted RL. Code runchu-tian/MiRL.'
last_reviewed: '2026-10-27'
papers:
- paper:mirl
recipes:
- recipe:mirl
claims:
- benchmark: 'Terminal-agent error-targeted RL vs generic env RL'
  metric: 'fix named misbehaviors then re-check'
  value: 'identifies weaknesses, trains to fix them, and checks they stay fixed'
  baseline: 'generic terminal-agent RL / CodeMidas-style env factory'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.35697'
  notes: 'Does not retarget method:codemidas.'
tags:
- rl-alignment
- terminal-agent
- active
---

# MiRL

## Method Overview
MiRL mines concrete terminal-agent misbehaviors, trains against those errors, and re-evaluates the same weaknesses instead of treating every trajectory as interchangeable env data.

## When to Use
- Terminal agents whose failures are specific and repeatable rather than a missing env factory.

## When NOT to Use
Default on `task:coding-agent-rl-environment-construction` remains `method:codemidas`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:codemidas`.

## Gotchas & Failure Modes
- Not a replacement for `method:codemidas`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
