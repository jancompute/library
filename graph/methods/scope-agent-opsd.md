---
id: method:scope-agent-opsd
type: method
title: 'SCOPE (agent critical-step OPSD)'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'programmatic checker AppWorld coverage / anti-drift'
  reason: 'CANOPY remains checker coverage; this SCOPE is critical-step agent OPSD'
  use_instead: method:canopy
- when: 'privileged-OPSD Fisher subspace (SCOPE-OPSD)'
  reason: 'method:scope-opsd is the Fisher-subspace auxiliary; this card is agent critical-step OPSD'
  use_instead: method:scope-opsd
assumptions:
- 'ALFWorld/WebShop-style agents. SFT warm-up then RL+OPSD. No public code as of 2026-10-30.'
last_reviewed: '2026-10-30'
papers:
- paper:scope-agent-opsd
recipes:
- recipe:scope-agent-opsd
claims:
- benchmark: 'ALFWorld / WebShop Qwen2.5-3B'
  metric: 'success rate'
  value: 'ALFWorld 97.7 / WebShop 85.2 vs SEED +5.9/+6.3pp; unseen ALFWorld 89.6 vs GRPO +23.2pp'
  baseline: 'SEED; GRPO'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.38391'
  notes: 'Does not retarget method:canopy. Distinct from method:scope-opsd.'
tags:
- opsd
- agent-rl
- active
---

# SCOPE (agent critical-step OPSD)

## Method Overview
SCOPE (this card) is agentic critical-step OPSD, not Fisher-subspace SCOPE-OPSD and not T2I SCOPE. The policy annotates its own traces, distills hindsight skills only at selected mistakes, and keeps a signed coefficient so distillation cannot flip RL advantages.

## When to Use
- Long-horizon agent RL where trajectory-level skills pollute unrelated steps.

## When NOT to Use
Checker coverage first hop remains `method:canopy`. Privileged Fisher SCOPE-OPSD is `method:scope-opsd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy` or `method:scope-opsd`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Slug is scope-agent-opsd because method:scope-opsd and method:scope-t2i already exist.
- No public code as of 2026-10-30.
