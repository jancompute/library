---
id: method:weir
type: method
title: Weir
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift or rubric credit)'
    reason: 'CANOPY remains coverage / anti-drift SOTA when a programmatic checker exists; Weir is prefix-tree shrinkage + watershed forks'
    use_instead: method:canopy
  - when: 'hindsight-guided tree exploration and turn-level credit for multi-turn LLM agents'
    reason: 'TreeHCA is hindsight tree credit; Weir is drift-aware prefix shrinkage plus Neyman budgets'
    use_instead: method:treehca
  - when: 'tree Root/Branch allocator plus sibling/observation-group advantages (TSBPO)'
    reason: 'TSBPO is sibling/observation-group credit; Weir is watershed forks on a discounted prefix tree'
    use_instead: method:tsbpo
  - when: 'variable environment latency / async stragglers, not sparse-outcome coverage'
    reason: 'SAO remains async straggler RL'
    use_instead: method:sao
assumptions:
  - 'Qwen2.5-3B/7B-Instruct. Multi-hop QA, ALFWorld, WebShop. 6 trajectories/task on QA, 8 on ALFWorld/WebShop; Weir uses M0=2/4 trunks and mean 4 branches (0.71–0.72× tokens). γ_hist=0.95, κ=0.4, λ_ζ=0.15, η=0.95. CAPO is not a library node. No public code as of 2026-11-23. Author names read as pseudonyms.'
last_reviewed: '2026-11-23'
papers:
- paper:weir
recipes:
- recipe:weir
claims:
- benchmark: 'Qwen2.5-3B/7B-Instruct vs CAPO on QA avg EM / ALFWorld / WebShop'
  metric: 'QA avg EM; ALFWorld success; WebShop; token ratio vs chain'
  value: '3B 32.18 / 84.83 / 78.47 vs CAPO 28.99 / 81.09 / 76.27; 7B 37.85 / 87.81 / 81.90 vs 35.63 / 84.33 / 80.40; 0.71–0.72× tokens'
  baseline: 'CAPO (Wang et al. 2604.18401); also GRPO / Turn-PPO'
  date: '2026-11-23'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.27570'
  notes: 'Three-seed 3B QA 32.18±0.28 vs CAPO 28.99±0.33. No public GitHub. CAPO is not a library node. Does not retarget CANOPY.'
tags:
- agent-rl
- credit-assignment
- prefix-tree
- multi-turn
- active
---

# Weir

## Method Overview
Weir keeps a cross-iteration canonical action-prefix tree with exponentially discounted visit counts. A prefix critic trains toward a minimax drift-aware shrinkage target: rare nodes use the trajectory return, dense nodes use a pooled mean. Task budgets follow Neyman \(B_q\propto\sqrt{\hat p_q(1-\hat p_q)}\). Within a task, extra branches go to watershed forks where survival-headroom uncertainty meets a steep value cliff.

## When to Use
- Multi-turn agents with one terminal binary reward, shared action prefixes across rollouts, and a budget of ~6–8 trajectories per task.

## When NOT to Use
Programmatic-checker coverage / anti-drift remains `method:canopy`. Hindsight tree credit remains `method:treehca`. Sibling/observation-group credit remains `method:tsbpo`. Async stragglers remain `method:sao`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:outcome-only-long-horizon-agent-rl`. Mention on `task:agentic-async-rl`. Distinct from CANOPY, TreeHCA, TSBPO, VSR, MPO. CAPO is a paper baseline, not a library node. Does **not** replace CANOPY.

## Gotchas & Failure Modes
- No public code at ingest (`code_status: none`).
- Author names read as pseudonyms; treat as preprint.
- Headline gaps are vs CAPO, not vs CANOPY AppWorld TGC.
