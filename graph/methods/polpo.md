---
id: method:polpo
type: method
title: POLPO
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'multi-reward GRPO aggregation (Pearson covariance or density-aware)'
    reason: 'CorrGRPO / DARA remain the aggregation first hop; POLPO is listwise likelihood over Pareto rankings'
    use_instead: method:corrgrpo
  - when: 'group Pareto-dominance reuse of conflict-filtered rollouts (GPDPO)'
    reason: 'GPDPO reuses filtered GRPO rollouts; POLPO maximizes probability of rankings consistent with Pareto dominance'
    use_instead: method:gpdpo
  - when: 'single-turn dense math/code Pass@1 RLVR (one verifier reward)'
    reason: 'CISPO remains Pass@1; POLPO needs multiple verifiers'
    use_instead: method:cispo
assumptions:
  - 'Several verifiers, partial success, incomparable conflicting outcomes. Extends DPO-style listwise likelihood to all complete rankings consistent with the Pareto partial order. Code generation and instruction following in the paper. No public code as of 2026-11-17.'
last_reviewed: '2026-11-17'
papers:
- paper:polpo
recipes:
- recipe:polpo
claims:
- benchmark: 'code generation and instruction following with multiple verifiers'
  metric: 'learning efficiency; complete requirement satisfaction vs scalar-reward training'
  value: 'improved learning efficiency and higher rates of complete requirement satisfaction vs scalar-reward aggregation (counts / weighted sums)'
  baseline: 'scalar complete-success reward; counts and weighted sums of verifier outcomes'
  date: '2026-11-17'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.19064'
  notes: 'Does not retarget method:corrgrpo / method:dara / method:gpdpo / method:cispo. Partial orders, not Pearson aggregation.'
tags:
- multi-reward
- pareto
- dpo
- active
---

# POLPO

## Method Overview
POLPO (Partial-Order Likelihood Policy Optimization) learns from multiple verifiers without collapsing them to a scalar. Pareto dominance marks responses that add satisfied requirements without losing any already held; conflicting subsets stay incomparable. The objective is the DPO-style listwise likelihood of every complete ranking consistent with that partial order, so verified improvements supervise before a complete solution exists.

## When to Use
- Code / IF RL with several requirement verifiers where a scalar sum compares incomparable partial successes.

## When NOT to Use
Pearson / density aggregation remains `method:corrgrpo` / `method:dara`. GRPO Pareto reuse remains `method:gpdpo`. One-verifier Pass@1 remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:multi-reward-rlvr`. Does **not** replace CorrGRPO / DARA.

## Gotchas & Failure Modes
- Incomparable responses must stay unranked; forcing a total order reintroduces the scalar bug.
- No public trainer as of 2026-11-17 (`code_status: none`).
