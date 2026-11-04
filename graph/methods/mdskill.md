---
id: method:mdskill
type: method
title: 'MDSkill'
category: agent-memory
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-memory'
  reason: 'ACE remains write-time playbook; MDSkill is multi-view OPSD of skills'
  use_instead: method:ace
assumptions:
- 'Skill-memory OPSD. Mention on task:outcome-only-long-horizon-agent-rl. Code announced as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:mdskill
recipes:
- recipe:mdskill
claims:
- benchmark: 'ALFWorld / WebShop'
  metric: 'success delta vs baseline memory'
  value: 'up to +7.1 / +8.1'
  baseline: 'single-view skill memory'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.05313'
  notes: 'Does not retarget method:ace or method:canopy. code_status: announced.'
tags:
- agent-memory
- opsd
- active
---

# MDSkill

## Method Overview
MDSkill writes skill memory from several views of the same trajectory via OPSD rather than a single write-time playbook bullet.

## When to Use
- Agent memory when a skill bank should be distilled from multi-view traces, not ACE incremental bullets.

## When NOT to Use
ACE remains the playbook default. CANOPY remains checker-protocol agent RL.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:ace`.

## Gotchas & Failure Modes
- Announced anonymous code, not a public GitHub.
