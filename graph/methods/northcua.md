---
id: method:northcua
type: method
title: 'NorthCUA'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:hybrid-computer-use-agent-rl'
  reason: 'RecreationWorld remains hybrid CUA train/eval'
  use_instead: method:recreationworld
- when: 'desktop/OS GUI ranking on OSWorld 2.0 paper protocol'
  reason: 'Claude computer-use remains the paper-protocol ranking'
  use_instead: method:claude-computer-use
assumptions:
- 'Nano/Mini/Pro CUA family. Official code beipo-ai/NorthCUA.'
last_reviewed: '2026-11-03'
papers:
- paper:northcua
recipes:
- recipe:northcua
claims:
- benchmark: 'GUI grounding, desktop execution, web interaction under reported settings'
  metric: 'open-source SOTA in the paper'
  value: 'SOTA among open-source models under the reported evaluation settings'
  baseline: 'open CUA baselines in the paper; not OSWorld 2.0 paper protocol'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.02102'
  notes: 'Code beipo-ai/NorthCUA. Does not retarget method:recreationworld or method:claude-computer-use.'
tags:
- cua
- flywheel
- active
---

# NorthCUA

## Method Overview
NorthCUA closes a loop between a task flywheel, a recording harness, verified trajectories, and staged mid-train / SFT / RL.

## When to Use
- Training an open CUA family from harvested executable experience rather than a recreation-oracle gym.

## When NOT to Use
RecreationWorld remains hybrid CUA first hop. Claude computer-use remains OSWorld 2.0 ranking.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:recreationworld` or `method:claude-computer-use`.

## Gotchas & Failure Modes
- Reported open-source SOTA is not OSWorld 2.0 paper protocol.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
