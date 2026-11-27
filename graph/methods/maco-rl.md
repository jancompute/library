---
id: method:maco-rl
type: method
title: Maco-RL
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'variable environment latency / async stragglers'
  reason: 'SAO remains async straggler replay; Maco-RL is quota MixRL plus tri-buffer sampling'
  use_instead: method:sao
- when: 'multi-stage agent capability stacking / continual learning'
  reason: 'ACLArena remains that first hop; Maco-RL is MixRL skill-add on a live host'
  use_instead: method:aclarena
- when: 'category see-saw on heterogeneous SWE RL'
  reason: 'Category-Aware SWE Experts remains that first hop; Maco-RL is not a category router'
  use_instead: method:category-aware-swe-experts
assumptions:
- 'verl + RLOO, G=8, 256 traj/update. TBS 20/60/20 Frontier/Reinforcement/History. Claw uniform partial credit; TMax excludes Solved. No public GitHub as of 2026-11-27.'
last_reviewed: '2026-11-27'
papers:
- paper:maco-rl
recipes:
- recipe:maco-rl
claims:
- benchmark: 'Qwen3.5-27B MixRL skill add (SWE-Verified / TB2.1 / GAIA2 / xbench-DeepSearch / HLE / BrowseComp / overall)'
  metric: 'overall then stage scores'
  value: '43.6 → S1 54.2 → S2 60.1'
  baseline: 'Qwen3.5-27B 60.2/12.0/40.5/67.4/3.0/37.9/43.6'
  date: '2026-11-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34703'
  notes: 'S1 71.4/51.3/52.4/67.0/6.0/28.6/54.2; S2 73.3/64.6/54.3/68.6/6.0/39.9/60.1. Does not retarget SAO, ACLArena, or Category-Aware SWE Experts. No public code.'
- benchmark: 'Qwen3.8-27B MixRL (SWE-Verified / TB2.1 / GAIA2 / xbench-DeepSearch / HLE / BrowseComp / overall)'
  metric: 'overall'
  value: '67.0 vs 61.4'
  baseline: 'Qwen3.8-27B host overall 61.4'
  date: '2026-11-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34703'
  notes: 'Maco-RL-3.8 74.5/55.2/72.3/79.0/12.0/54.2/67.0.'
tags:
- rl-alignment
- agentic
- mixrl
- continual-learning
- active
---

# Maco-RL

## Method Overview
Maco-RL samples each MixRL update from three on-policy buckets: Frontier (zero successes in the group), Reinforcement (mixed), History (all successes). Default quotas 20/60/20. TMax drops already-solved tasks from the live mix; Claw is uniform partial credit rather than a sparse binary. Host is verl RLOO, not SAO's async straggler buffer.

## When to Use
- Adding a new agent skill on a live MixRL host when old-task collapse is the complaint, not tool-latency stragglers.

## When NOT to Use
Async stragglers remain SAO. Agent continual-learning first hop remains ACLArena. Heterogeneous SWE category see-saw remains Category-Aware SWE Experts.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:sao`, `method:aclarena`, or `method:category-aware-swe-experts`.

## Gotchas & Failure Modes
- Uniform MixRL without TMax / TBS can collapse BrowseComp while lifting TB2.1.
- No public train code as of 2026-11-27.
- Not a SAO bake-off and not an ACLArena LoRA-expert recipe.
