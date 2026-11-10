---
id: method:care-po
type: method
title: 'CARE-PO (Controllable Tool-Call Efficiency)'
category: rl-algorithm
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'outcome-only long-horizon agent RL (AppWorld coverage / anti-drift)'
  reason: 'CANOPY remains sparse-outcome coverage; CARE-PO is a tool-budget efficiency plug-in'
  use_instead: method:canopy
- when: 'train a live-web multi-hop search agent (SFT-RL climbing)'
  reason: 'Iris remains the search-agent recipe; CARE-PO is a call-count anchor on a GRPO host'
  use_instead: method:iris
assumptions:
- 'Tool-using agent with a countable call budget. Paper: GAIA operating-point grid; 27B efficiency-reward collapse ablation. No public code as of 2026-11-10. arXiv 2611.12125 above watermark 2611.09634.'
last_reviewed: '2026-11-10'
papers:
- paper:care-po
recipes:
- recipe:care-po
claims:
- benchmark: 'GAIA operating-point grid + 27B efficiency-reward collapse'
  metric: 'success vs call count; collapse to zero calls'
  value: '5/6 GAIA points improve success and calls; sixth matches success at 58.6% fewer calls; 27B efficiency-reward collapses to zero calls, CARE-PO does not'
  baseline: 'GRPO / learned efficiency-reward'
  date: '2026-11-10'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.12125'
  notes: 'Does not retarget method:canopy or method:iris.'
tags:
- agentic
- efficiency
- tool-use
- active
---

# CARE-PO (Controllable Anchored Relative Efficiency PO)

## Method Overview
CARE-PO keeps a GRPO host and scores tool-call count against a fixed per-task reference budget. The advantage is relative to that budget, so a learned efficiency head cannot reward zero-call collapse.

## When to Use
- Tool-using agents where an efficiency reward collapsed the policy to empty traces.

## When NOT to Use
AppWorld coverage remains `method:canopy`. Live-web search training remains `method:iris`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:outcome-only-long-horizon-agent-rl` with a mention on `task:web-search-agent-rl`. Does **not** replace CANOPY or Iris.

## Gotchas & Failure Modes
- No public trainer.
- The reference budget is a hyperparameter per task; a global call penalty is not this method.
- Not an AppWorld TGC ranking.
