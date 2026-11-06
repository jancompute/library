---
id: method:harness-s
type: method
title: 'Harness-S (Sibling-Harness Rescue)'
category: agents
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-harness-runtime'
  reason: 'omp2 remains the production harness kernel; Harness-S is sibling-harness rescue during policy GRPO'
  use_instead: method:omp2-harness
- when: 'MCTS full-harness search (HarnessFlow)'
  reason: 'HarnessFlow searches harnesses; Harness-S freezes a sibling pool and trains the policy'
  use_instead: method:harnessflow
- when: 'population co-evolution of executable harnesses with a shared policy (CoHARL)'
  reason: 'CoHARL rewrites harnesses while the policy trains; Harness-S keeps the sibling pool frozen'
  use_instead: method:coharl
- when: 'multi-model all-fail salvage by peer trajectory exchange (GRAFT)'
  reason: 'GRAFT swaps peer-model traces; Harness-S re-rolls the same policy under sibling harnesses'
  use_instead: method:graft
- when: 'distill optimized-harness behaviors into weights under a fixed target harness'
  reason: 'Harness-Zero is agent-as-harness SFT; Harness-S is GRPO with rescue rollouts'
  use_instead: method:harness-zero
- when: 'AppWorld coverage / anti-drift without a sibling-harness pool'
  reason: 'CANOPY remains checker coverage; Harness-S needs a frozen sibling pool'
  use_instead: method:canopy
assumptions:
- 'Frozen sibling-harness pool during policy GRPO. Rescue only all-fail groups. Transfer evaluated under H0. Code DeepExperience/Harness-S. HF Daily 2026-11-06 leftover (2611.04277).'
last_reviewed: '2026-11-06'
papers:
- paper:harness-s
recipes:
- recipe:harness-s
claims:
- benchmark: 'Qwen3.5-4B AppWorld / SWE-Gym / DBBench, Table 1 H0'
  metric: 'Pass@3 / Avg@3 vs GRPO and GRPO+H0-rescue'
  value: 'AppWorld 67.56±1.87 / 56.87±1.47; SWE-Gym 38.75±2.22 / 28.75±1.73; DBBench 73.33±2.36 / 71.00±1.84'
  baseline: 'GRPO AppWorld 60.31 / 48.98; GRPO+H0-rescue 61.83 / 51.91'
  date: '2026-11-06'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.04277'
  notes: 'Does not retarget method:omp2-harness or method:canopy. Distinct from method:harnessflow / method:coharl / method:graft.'
- benchmark: 'Qwen3.5-9B AppWorld Table 1 H0 vs rank-1'
  metric: 'Pass@3 / Avg@3'
  value: 'H0 72.52±1.65 / 62.34±1.28; rank-1 75.19±1.56 / 67.05±1.20'
  baseline: 'GRPO H0 64.89 / 53.31'
  date: '2026-11-06'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.04277'
  notes: 'Rank-1 routing after training, including H0 in the pool.'
tags:
- agents
- harness
- grpo
- active
---

# Harness-S (Sibling-Harness Rescue)

## Method Overview
Harness-S trains a policy with GRPO under a frozen target harness $H_0$ and a frozen sibling-harness pool. When a group is all-fail, it re-rolls the same policy under a rank-1 sibling, keeps source advantages on accepted replacements, and later evaluates the updated policy under $H_0$. The sibling pool is not rewritten during the policy update.

## When to Use
- Agentic GRPO where all-fail groups starve the update and you can hold a fixed sibling-harness pool (not a second model).

## When NOT to Use
Default on `task:agent-harness-runtime` remains `method:omp2-harness`. Coverage without siblings remains `method:canopy`. Peer-model salvage is `method:graft`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:omp2-harness`, `method:canopy`, `method:harnessflow`, `method:coharl`, `method:graft`, or `method:harness-zero`. Mention on `task:outcome-only-long-horizon-agent-rl`.

## Gotchas & Failure Modes
- Needs a sibling pool; mixed-harness GRPO without rescue underfits Table 1.
- Transfer is under $H_0$; rank-1 routing is an extra eval, not the production kernel.
