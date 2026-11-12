---
id: method:booknavigator
type: method
title: BookNavigator
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'olympiad-style natural-language proofs / IMO TTC rather than Pass@1'
    reason: 'Nemotron IMO Gold remains the olympiad TTC first hop; BookNavigator is textbook-study RL'
    use_instead: method:nemotron-imo-gold
  - when: 'dumped corpus ≫ window'
    reason: 'RLM remains dumped-corpus offload; BookNavigator is an RL study interface over a textbook'
    use_instead: method:rlm
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; BookNavigator is long-horizon textbook study, not a Pass@1 loss'
    use_instead: method:cispo
  - when: 'trained compaction notes inside a 20K window (MEMENTO)'
    reason: 'MEMENTO is trained compaction; BookNavigator navigates pages instead of compacting them'
    use_instead: method:memento
assumptions:
  - 'A long textbook plus a page/section action interface. Paper: Intern-S2-Preview-35B. No public GitHub as of 2026-11-12. HF Daily 2026-11-12 leftover. arXiv 2610.39671.'
last_reviewed: '2026-11-12'
papers:
- paper:booknavigator
recipes:
- recipe:booknavigator
claims:
- benchmark: 'Intern-S2-Preview-35B textbook-study proof accuracy'
  metric: 'proof accuracy vs textbook-free / fixed-context RL'
  value: '51.5%→79.5%'
  baseline: 'textbook-free RL / fixed-context RL'
  date: '2026-11-12'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.39671'
  notes: 'Does not retarget method:nemotron-imo-gold, method:rlm, or method:cispo. No public code as of 2026-11-12. HF Daily 2026-11-12 leftover.'
tags:
- olympiad
- rlvr
- long-context
- active
---

# BookNavigator

## Method Overview
BookNavigator is textbook-study RL. The policy acts over pages and sections of a long textbook, receives fine-grained study rewards (progress, coverage, retrieval of cited lemmas), then is evaluated on downstream proofs. The textbook is an environment, not a dumped prompt.

## When to Use
- Olympiad or textbook-grounded proof training where the source is a long book the model should study, not a 1M-token dump and not IMO TTC.

## When NOT to Use
Olympiad TTC remains `method:nemotron-imo-gold`. Dumped-corpus offload remains `method:rlm`. Pass@1 remains `method:cispo`. Trained compaction remains `method:memento`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:olympiad-math-posttrain`. Mention on `task:long-context-prompt-offload`. Does **not** replace Nemotron IMO Gold or RLM.

## Gotchas & Failure Modes
- No public trainer as of 2026-11-12.
- Study rewards are not a Pass@1 verifier. Do not drop the downstream proof eval.
- A dumped textbook in the prompt is not this method.
