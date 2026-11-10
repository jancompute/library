---
id: method:aes
type: method
title: 'AES (Adaptive Entropy-Sparing)'
category: rl-algorithm
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'single-turn dense math/code Pass@1 RLVR'
  reason: 'CISPO remains Pass@1; AES is a GRPO-host length plug-in'
  use_instead: method:cispo
- when: 'local continue-vs-conclude length control (LoCo; not Pass@1 CISPO)'
  reason: 'LoCo is token-level continue/conclude; AES is entropy-sparing on correct rollouts'
  use_instead: method:loco
assumptions:
- 'GRPO-family host with a correctness verifier. Paper: DeepSeek-R1-Distill-Qwen 1.5B/7B. GitHub MobiusDai/AES 404 as of 2026-11-10. Sibling of LoCo / When2Think / LSD. arXiv 2611.11901 above watermark 2611.09634.'
last_reviewed: '2026-11-10'
papers:
- paper:aes
recipes:
- recipe:aes
claims:
- benchmark: 'DeepSeek-R1-Distill-Qwen 1.5B/7B math mean'
  metric: 'accuracy / mean length vs GRPO'
  value: '1.5B 64.9→68.7 (+3.8), len 6467→3048 (−52.9%); 7B 74.1→75.2, 4712→2510'
  baseline: 'GRPO / length-penalty hosts'
  date: '2026-11-10'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.11901'
  notes: 'Does not retarget method:cispo. Sibling of method:loco / method:when2think / method:lsd.'
tags:
- rlvr
- length-control
- entropy
- active
---

# AES (Adaptive Entropy-Sparing)

## Method Overview
AES keeps a GRPO host and sparsifies high-entropy tokens only on already-correct rollouts. Failed rollouts keep entropy so the policy can still explore.

## When to Use
- Dense math RLVR where length exploded and a simple length penalty hurt accuracy.

## When NOT to Use
Pass@1 default remains `method:cispo`. Token-level continue/conclude remains `method:loco`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:math-code-rl-dense`. Does **not** replace CISPO.

## Gotchas & Failure Modes
- GitHub MobiusDai/AES 404 as of 2026-11-10 (`code_status: announced`).
- Sibling of LoCo / When2Think / LSD, not a replacement of any of them.
- Needs a correctness verifier; not a process reward.
