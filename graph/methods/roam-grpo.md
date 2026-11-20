---
id: method:roam-grpo
type: method
title: ROAM-GRPO
category: rl-algorithm
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'Pass@K / coverage / no-backward rather than Pass@1'
    reason: 'ES-reasoning remains the Pass@K first hop; ROAM is a GRPO-host diversity plug-in'
    use_instead: method:es-reasoning
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; ROAM is coverage/diversity on a GRPO host'
    use_instead: method:cispo
  - when: 'group-dependent coverage rewards / Team-GRPO (not ES-reasoning)'
    reason: 'Team-GRPO is group-dependent rewards; ROAM is embedding-distance novelty'
    use_instead: method:team-grpo
  - when: 'Pass@K tree-rollout coverage'
    reason: 'DATPO is difficulty-adaptive trees; ROAM is embedding novelty on GRPO'
    use_instead: method:datpo
assumptions:
  - 'Qwen3.5-2B MATH lvl5 1000-problem subset. No public code as of 2026-11-20. Distinct from method:team-grpo / method:dart-es / method:datpo.'
last_reviewed: '2026-11-20'
papers:
- paper:roam-grpo
recipes:
- recipe:roam-grpo
claims:
- benchmark: 'Qwen3.5-2B MATH lvl5 (1000-problem subset)'
  metric: 'pass@16 / embedding distance'
  value: '+4.7% pass@16 vs GRPO; 1.5–2× embedding distance'
  baseline: 'GRPO'
  date: '2026-11-20'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.25926'
  notes: 'Subset, not full MATH. No public code. Does not retarget method:es-reasoning / method:cispo.'
tags:
- rlvr
- passk
- roam
- diversity
- active
---

# ROAM-GRPO

## Method Overview
ROAM adds an embedding-distance novelty term to GRPO advantages so the policy keeps distinct solutions while training pass@1.

## When to Use
- GRPO-family coverage when you measure pass@k and can score rollout embeddings.

## When NOT to Use
Pass@K first hop remains `method:es-reasoning`. Pass@1 remains `method:cispo`. Group-dependent rewards remain `method:team-grpo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:passk-reasoning-coverage`. Mention on `task:math-code-rl-dense`. Does **not** replace ES-reasoning or CISPO.

## Gotchas & Failure Modes
- +4.7% is on a 1000-problem MATH lvl5 subset, not the full benchmark.
- No public code as of 2026-11-20.
- Embedding novelty is not a verifier; it can reward wrong-but-different traces.
