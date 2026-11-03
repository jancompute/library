---
id: method:memento
type: method
title: 'MEMENTO'
category: agent-recursion
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:long-context-prompt-offload'
  reason: 'RLM remains dumped-corpus offload; MEMENTO is trained compaction inside a 20K window'
  use_instead: method:rlm
assumptions:
- 'Qwen3-8B book-level QA, books to 2.5M tokens, context cap 20K. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:memento
recipes:
- recipe:memento
claims:
- benchmark: 'four book-level QA benches, books up to 2.5M tokens'
  metric: 'accuracy at <=20K context'
  value: 'Qwen3-8B 36.9% to 67.8%; GPT-5.5 agent 13.1% / full-book 56.7%; GLM-5.3 agent 69.3%'
  baseline: 'untrained Qwen3-8B; GPT-5.5 agent and full book; GLM-5.3 agent and full context'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.00244'
  notes: 'Does not retarget method:rlm.'
tags:
- long-context
- compaction
- agents
- active
---

# MEMENTO

## Method Overview
MEMENTO trains a Qwen3-8B agent to write compaction notes: hindsight-annotated SFT, then RL on correctness, note quality, and calibration, never holding more than 20K tokens.

## When to Use
- Dumped long documents that must be processed inside a small window via learned notes rather than a REPL offload.

## When NOT to Use
RLM remains the dumped-corpus first hop. TACM remains the trained 8K self-call / range-read harness.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:rlm` or `method:tacm`.

## Gotchas & Failure Modes
- Compaction notes are not a REPL over the raw corpus.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
