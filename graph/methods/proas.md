---
id: method:proas
type: method
title: 'ProAS'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:outcome-only-long-horizon-agent-rl when a checker exists'
  reason: 'CANOPY remains checker coverage; ProAS reshapes group advantages with a reference graph'
  use_instead: method:canopy
- when: 'variable environment latency / async stragglers'
  reason: 'SAO remains async; ProAS is critic-free credit shaping'
  use_instead: method:sao
assumptions:
- 'Multi-turn critic-free agent RL. Code LINs-lab/ProAS.'
last_reviewed: '2026-10-27'
papers:
- paper:proas
recipes:
- recipe:proas
claims:
- benchmark: 'Qwen2.5-1.5B/7B-Instruct ALFWorld / WebShop vs group RL hosts'
  metric: 'success rate; convergence'
  value: 'ALFWorld 91.9/94.3; WebShop 66.7/70.8; up to 2.44x faster convergence'
  baseline: 'group-based agentic RL without ARG shaping'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.18683'
  notes: 'Does not retarget method:canopy. SKIPPED 2026-10-14; ingested 2026-10-27.'
tags:
- rl-alignment
- agentic
- active
---

# ProAS

## Method Overview
ProAS builds an Agentic Reference Graph and reshapes group advantages so winner traces do not reinforce structurally unreasonable actions and loser traces penalize the steps that actually diverted.

## When to Use
- Multi-turn critic-free GRPO-family agent RL with uniform trajectory credit.

## When NOT to Use
Default on `task:outcome-only-long-horizon-agent-rl` remains `method:canopy`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy`.

## Gotchas & Failure Modes
- Not a replacement for `method:canopy`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
