---
id: method:opsd4mas
type: method
title: OPSD4MAS
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains reverse-KL matching; OPSD4MAS is privileged communication credit on a GRPO host'
    use_instead: method:opd
  - when: 'Leader-Searcher-Answerer hierarchical OPD (MultiAgent-OPD), not communication-as-credit'
    reason: 'MultiAgent-OPD distills a role hierarchy; OPSD4MAS turns messages into token-level OPSD credit'
    use_instead: method:multiagent-opd
  - when: 'wanting a multi-agent crew as the communication layer'
    reason: 'MAS default remains single-agent-plus-tools; OPSD4MAS is a credit overlay, not an orchestration default'
    use_instead: method:single-agent-plus-tools
assumptions:
  - 'Multi-agent GRPO with inspectable communication traces. Code Camel-Prince/OPSD4MAS on verl as of 2026-11-13.'
last_reviewed: '2026-11-13'
papers:
- paper:opsd4mas
recipes:
- recipe:opsd4mas
claims:
- benchmark: 'MATH pass@4 vs GRPO; FW4 six-bench mean pass@1 vs GRPO/DAPO'
  metric: 'pass@4; mean pass@1'
  value: 'MATH pass@4 up to +20.00 vs GRPO; mean pass@1 +8.87 vs GRPO / +6.14 vs DAPO (FW4, six benches)'
  baseline: 'GRPO / DAPO'
  date: '2026-11-13'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.16206'
  notes: 'Does not retarget method:opd or method:single-agent-plus-tools. Distinct from method:multiagent-opd. Code Camel-Prince/OPSD4MAS released (verl). Mention on task:multi-agent-orchestration.'
tags:
- distillation
- opsd
- multi-agent
- grpo
- active
---

# OPSD4MAS

## Method Overview
OPSD4MAS turns future multi-agent messages into token-level on-policy self-distillation credit. Facts are extracted from communication, associated to tokens, filtered by leave-one-out, and annealed jointly with GRPO. The outcome reward stays; communication is no longer a scalar team bonus.

## When to Use
- Multi-agent GRPO where messages are inspectable and scalar communication rewards are too coarse.

## When NOT to Use
Single-teacher matching remains `method:opd`. Hierarchical team OPD remains `method:multiagent-opd`. Orchestration default remains `method:single-agent-plus-tools`. AppWorld coverage remains `method:canopy`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Mention on `task:multi-agent-orchestration`. Does **not** replace OPD or single-agent-plus-tools.

## Gotchas & Failure Modes
- Needs real communication traces; collapsing MAS to a single agent removes the privilege.
- Anneal the OPSD term; a full-weight joint can overfit message style.
- Distinct from MultiAgent-OPD's Leader-Searcher-Answerer roles.
