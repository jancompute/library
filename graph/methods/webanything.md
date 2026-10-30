---
id: method:webanything
type: method
title: 'WebAnything'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'hybrid GUI+code recreation train/eval'
  reason: 'RecreationWorld remains that first hop; WebAnything reconstructs wild-web envs'
  use_instead: method:recreationworld
- when: 'desktop/OS GUI ranking on OSWorld 2.0 paper protocol'
  reason: 'Claude computer-use remains that ranking; WebAnything is web env reconstruction'
  use_instead: method:claude-computer-use
assumptions:
- 'Browser-observable websites. Official code china-qijizhifeng/Web-Anything.'
last_reviewed: '2026-10-30'
papers:
- paper:webanything
recipes:
- recipe:webanything
claims:
- benchmark: 'reconstructed web envs; Qwen3.5-9B REAL'
  metric: 'site count / REAL delta'
  value: '244 sites / 12,984 executed tasks; Qwen3.5-9B REAL +9.9pp'
  baseline: 'human-assisted mirrors; generative site construction; capture-and-replay'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.37786'
  notes: 'Does not retarget method:recreationworld.'
tags:
- cua
- env
- active
---

# WebAnything

## Method Overview
WebAnything turns live URLs into reusable web-agent environments. Capture observable structure, freeze a candidate, verify it, and repair or recapture instead of writing a per-site harness.

## When to Use
- Web-agent RL that needs many resettable real-site envs without a human mirror per domain.

## When NOT to Use
Hybrid GUI+code recreation first hop remains RecreationWorld. OSWorld 2.0 ranking remains Claude computer-use.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:recreationworld` or `method:claude-computer-use`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Web sites, not desktop OSWorld ranking.
- Authorization still needed for some captures.
