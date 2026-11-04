---
id: method:toolspace
type: method
title: 'ToolSpace'
category: training-systems
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the first hop on task:coding-agent-rl-environment-construction'
  reason: 'CodeMidas remains source-code env factory; ToolSpace is MCP-trace tool envs'
  use_instead: method:codemidas
assumptions:
- 'MCP traces exist. Mention beside SynthAPI / VHD-Play. Code released as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:toolspace
recipes:
- recipe:toolspace
claims:
- benchmark: 'Qwen3.6-35B-A3B / GLM-5.2 tool-use'
  metric: 'success after SFT / RL'
  value: 'Qwen3.6-35B-A3B 23.0 to 41.0 (43.2 RL); GLM-5.2 44.6 to 56.6'
  baseline: 'unadapted tool-use policy'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.05036'
  notes: 'Does not retarget method:codemidas. Distinct from method:synthapi / method:vhd-play.'
tags:
- environments
- tool-use
- active
---

# ToolSpace

## Method Overview
ToolSpace builds tool-centric RL environments from real MCP traces instead of from repository source.

## When to Use
- Coding/tool-agent RL when the bottleneck is MCP-tool coverage rather than issue-to-patch from source.

## When NOT to Use
CodeMidas remains the source-code env factory. VHD-Play remains mechanism-first tools. SynthAPI remains controllable synthetic APIs.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:codemidas`.

## Gotchas & Failure Modes
- Needs MCP traces; not a SWE issue synthesizer.
