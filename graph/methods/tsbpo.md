---
id: method:tsbpo
type: method
title: 'TSBPO'
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:outcome-only-long-horizon-agent-rl'
  reason: 'CANOPY remains checker coverage; TSBPO is a tree allocator plus sibling/observation-group credit'
  use_instead: method:canopy
- when: 'variable environment latency / async stragglers'
  reason: 'SAO remains async straggler replay; TSBPO is outcome-only tree credit'
  use_instead: method:sao
assumptions:
- 'Interactive agent RL from terminal outcomes with replayable physical trees. No public code as of 2026-11-02.'
last_reviewed: '2026-11-02'
papers:
- paper:tsbpo
recipes:
- recipe:tsbpo
claims:
- benchmark: 'Qwen2.5-1.5B ALFWorld / WebShop'
  metric: 'stochastic success'
  value: 'ALFWorld 97.79 seen / 96.64 unseen; WebShop 81.07 on 500 test goals x 6 episodes'
  baseline: 'step-term ablation WebShop 75.93 at update-100; CANOPY AppWorld ranking is a different protocol'
  date: '2026-11-02'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.41697'
  notes: 'Does not retarget method:canopy.'
tags:
- agent-rl
- tree
- active
---

# TSBPO

## Method Overview
TSBPO is a tree-structured sampling-to-update loop: a Root/Branch allocator spends a fixed rollout budget on contrasting continuations, sibling trajectory advantages and observation-group step advantages assign delayed credit, and the actor sums clipped token surrogates over complete responses then normalizes across active turns.

## When to Use
- Outcome-only interactive agent RL when you can replay physical trees and need to decide which task/state continuations to sample under a fixed budget.

## When NOT to Use
CANOPY remains checker coverage. SAO remains async stragglers.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:canopy` or `method:sao`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-11-02; no locked-SOTA bake-off against CANOPY AppWorld.
- Avoid response-length averaging in the policy-gradient term; TSBPO normalizes across active turns instead.
- No public code as of 2026-11-02.
