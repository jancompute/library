---
id: method:hive-mem
type: method
title: HiVe-Mem
category: agents
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'write-time playbook / incremental bullet memory'
    reason: 'ACE remains the playbook default; HiVe-Mem is multimodal retrieval with horizontal expansion and vertical evidence composition'
    use_instead: method:ace
  - when: 'evidence-linked memory / WikiTrace (not write-time playbook)'
    reason: 'WikiTrace links insights to raw trajectories; HiVe-Mem is multimodal expansion plus a trainable selector'
    use_instead: method:wikitrace
  - when: 'synthetic single-stage pretrain from Wikipedia/Wikibooks seeds (Hive-Synth)'
    reason: 'Hive-Synth is pretrain data; HiVe-Mem is agent memory. Distinct slugs.'
    use_instead: method:hive-synth
assumptions:
  - 'Multimodal agents with a long interaction history and a retrievable memory store. Paper: Qwen3-VL-4B. Code ViktorAxelsen/HiVe-Mem as of 2026-11-13. Distinct from method:hive-synth.'
last_reviewed: '2026-11-13'
papers:
- paper:hive-mem
recipes:
- recipe:hive-mem
claims:
- benchmark: 'Qwen3-VL-4B multimodal agent memory; token budget vs uncompressed history'
  metric: 'F1 / LJ; memory tokens'
  value: 'F1/LJ 32.32/57.96; 0.658M vs 7.812M tokens (~90% cut)'
  baseline: 'uncompressed history / compressed semantic memory'
  date: '2026-11-13'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.12872'
  notes: 'Does not retarget method:ace. Distinct from method:hive-synth and method:wikitrace. Tuesday leftover (2611.12872). Code ViktorAxelsen/HiVe-Mem released.'
tags:
- agent-memory
- multimodal
- retrieval
- active
---

# HiVe-Mem

## Method Overview
HiVe-Mem is multimodal agent memory that interleaves horizontal expansion (neighboring memories, not one compressed hit) with vertical evidence composition, then a trainable selector. On Qwen3-VL-4B it reports F1/LJ 32.32/57.96 at 0.658M tokens versus 7.812M uncompressed (~90% cut).

## When to Use
- Multimodal agents whose queries need heterogeneous evidence from a long history, not a write-time playbook.

## When NOT to Use
Write-time playbooks remain `method:ace`. Evidence-linked trajectory memory remains `method:wikitrace`. Synthetic pretrain data remains `method:hive-synth`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:agent-memory`. Does **not** replace ACE. Distinct from `method:hive-synth`.

## Gotchas & Failure Modes
- Slug collision risk with Hive-Synth; this is memory, not pretrain data.
- Trainable selector needs query-labeled evidence; a frozen playbook is cheaper when text-only ACE is enough.
