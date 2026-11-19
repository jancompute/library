---
id: method:eca
type: method
title: ECA
category: rl-algorithm
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'train a live-web multi-hop search agent (SFT-RL climbing)'
    reason: 'Iris remains the search-agent first hop; ECA is evidence-potential credit on a GRPO host'
    use_instead: method:iris
  - when: 'grounded credit assignment for search vs answer tokens (GCA)'
    reason: 'GCA splits search vs answer tokens; ECA is evidence-only Φ(D) from retrieved documents'
    use_instead: method:gca
  - when: 'evidence-guided step credit for deep-search agents (EG-GRPO)'
    reason: 'EG-GRPO is evidence-claim step credit; ECA is an evidence-only potential plus Horizon/TD/MC'
    use_instead: method:eg-grpo
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; ECA is search-agent credit'
    use_instead: method:cispo
assumptions:
  - 'Multi-hop search agent with retrieved documents. GRPO host. Paper: Qwen2.5-3B/7B. Distinct from GCA / EG-GRPO / Iris. No public train code as of 2026-11-19 (Snowball0823/ECA is unrelated).'
last_reviewed: '2026-11-19'
papers:
- paper:eca
recipes:
- recipe:eca
claims:
- benchmark: 'Deep-search QA (Qwen2.5-3B/7B vs GRPO)'
  metric: 'macro EM'
  value: '3B 45.80 vs GRPO 44.77 (+1.03); 7B 51.60 vs GRPO 46.80 (+4.80)'
  baseline: 'GRPO'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.23824'
  notes: 'Does not retarget method:iris / method:gca / method:eg-grpo. code_status none.'
tags:
- credit-assignment
- search-agent
- evidence
- grpo
- active
---

# ECA

## Method Overview
Evidence-based Credit Assignment (ECA) scores intermediate search steps from retrieved-document evidence Φ(D), not from the final answer. ECA-Horizon, ECA-TD, and ECA-MC instantiate the potential on a GRPO host.

## When to Use
- Deep-search agent RL when outcome GRPO starves intermediate retrieval steps.

## When NOT to Use
Search-agent first hop remains `method:iris`. Search-vs-answer token split remains `method:gca`. Evidence-claim step credit remains `method:eg-grpo`. Pass@1 math/code remains `method:cispo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:web-search-agent-rl`. Does **not** replace Iris.

## Gotchas & Failure Modes
- Snowball0823/ECA is an unrelated repo.
- No public train code (`code_status: none`).
