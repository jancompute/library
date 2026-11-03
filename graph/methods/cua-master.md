---
id: method:cua-master
type: method
title: 'CUA-Master'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:hybrid-computer-use-agent-rl'
  reason: 'RecreationWorld remains hybrid CUA train/eval; CUA-Master is a nested flywheel recipe'
  use_instead: method:recreationworld
- when: 'desktop/OS GUI ranking on OSWorld 2.0 paper protocol'
  reason: 'Claude computer-use remains the paper-protocol ranking'
  use_instead: method:claude-computer-use
assumptions:
- '27B GUI+CLI CUA. Mention on task:computer-use-agent. Official code xlyu0106/CUA-Master.'
last_reviewed: '2026-11-03'
papers:
- paper:cua-master
recipes:
- recipe:cua-master
claims:
- benchmark: 'OSWorld Verified / OSWorld 2.0, 27B'
  metric: 'success'
  value: '80.2 OSWorld Verified; 36.9 OSWorld 2.0'
  baseline: 'prior open CUA recipes in the paper; not Claude paper-protocol 20.6% binary'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03126'
  notes: 'Code xlyu0106/CUA-Master. Does not retarget method:recreationworld or method:claude-computer-use.'
tags:
- cua
- hybrid
- active
---

# CUA-Master

## Method Overview
CUA-Master grows CUA data from instructional-video seeds and model weaknesses, then trains a 27B GUI+CLI policy with snapshot-rollback retries.

## When to Use
- Training a hybrid GUI+code CUA from open-world video and recursive task synthesis.

## When NOT to Use
RecreationWorld remains hybrid CUA train/eval first hop. Claude computer-use remains OSWorld 2.0 paper-protocol ranking.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:recreationworld` or `method:claude-computer-use`.

## Gotchas & Failure Modes
- OSWorld 2.0 36.9 is not a paper-protocol bake-off against Claude 20.6% binary.
- OSWorld Verified is not OSWorld 2.0 ranking.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
