---
id: method:synthapi
type: method
title: 'SynthAPI'
category: training-systems
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:coding-agent-rl-environment-construction'
  reason: 'CodeMidas remains the OSS-source env factory; SynthAPI is a controllable synthetic tool-use env generator with a scaling law over 849 models'
  use_instead: method:codemidas
- when: 'compute-optimal agentic RL env/task/trajectory allocation'
  reason: 'Agentic RL Data Scaling allocates existing envs; SynthAPI synthesizes tool/task/database diversity'
  use_instead: method:agentic-rl-data-scaling
assumptions:
- '458,752 synthetic tasks, 849 trained models, four sizes. Controls: tools, tasks, databases. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:synthapi
recipes:
- recipe:synthapi
claims:
- benchmark: 'Downstream tool-use agent generalization vs synthesized env composition; 849 models'
  metric: 'scaling-law prediction of generalization from tool/task/database diversity'
  value: 'as data budgets grow, scaling tool and database diversity beats adding more tasks of the same tools; composition predicts downstream tool-use generalization'
  baseline: 'task-count scaling with fixed tool/database diversity'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37648'
  notes: 'Does not retarget method:codemidas.'
tags:
- training-systems
- agents
- data
- active
---

# SynthAPI

## Method Overview
SynthAPI synthesizes tool-use environments with explicit controls on tools, tasks, and the databases those tools touch. A scaling law from 849 models says tool and database diversity start to dominate task count as the data budget grows.

## When to Use
- Building synthetic tool-use RL data and you would otherwise scale task count on a small tool/API set.

## When NOT to Use
Default on `task:coding-agent-rl-environment-construction` remains `method:codemidas`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:codemidas`.

## Gotchas & Failure Modes
- Not a replacement for `method:codemidas`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
