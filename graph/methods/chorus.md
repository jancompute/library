---
id: method:chorus
type: method
title: Chorus
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the ~7B dense pretrain optimizer'
    reason: 'Muon2 remains the 7B optimizer; Chorus is shared n-gram tables plus layer-wise rescale'
    use_instead: method:muon2
  - when: 'open pretrain mix / Dolma-3 recipe'
    reason: 'OLMo-3 remains the open mix; Chorus is an n-gram embedding module'
    use_instead: method:olmo-3
  - when: 'standard dense ~7B NTP from scratch on web/open data'
    reason: 'Muon2+OLMo-3 remain the 7B default; Chorus is a table architecture plug-in'
    use_instead: method:muon2
assumptions:
  - 'N-gram hash tables shared across layers with per-layer rescale/project. Paper: 17.1M–9.6B ClimbMix/FineWeb/DCLM. Code dualverse-ai/chorous (typo in repo name) as of 2026-11-19. Ember is table-optimizer-state compression, not a Muon replacement.'
last_reviewed: '2026-11-19'
papers:
- paper:chorus
recipes:
- recipe:chorus
claims:
- benchmark: 'ClimbMix 1.2B vs 9.6B Engram/FactorEngram tables'
  metric: 'val BPB'
  value: '0.9229 vs larger-table Engram/FactorEngram (87% smaller tables)'
  baseline: 'Engram / FactorEngram at 9.6B tables'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.23386'
  notes: 'Does not retarget method:muon2 / method:olmo-3. Code dualverse-ai/chorous.'
- benchmark: 'ClimbMix 9.6B Chorus vs FactorEngram / Engram'
  metric: 'val BPB'
  value: '0.9148 vs FactorEngram 0.9258 / Engram 0.9273'
  baseline: 'FactorEngram / Engram'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.23386'
  notes: 'Does not retarget Muon2. Ember −99.2% table-optimizer mem (1.2B 4.47 GiB→35.7 MiB).'
tags:
- ngram
- embedding
- pretrain
- memory
- active
---

# Chorus

## Method Overview
Chorus stores n-grams in shared hash tables and rescales/projects them per layer. Ember compresses table optimizer state.

## When to Use
- Dense pretrain when n-gram tables help but per-layer Engram-style tables are too large.

## When NOT to Use
7B optimizer remains `method:muon2`. Open mix remains `method:olmo-3`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:pretrain-dense-7b`. Mention on `task:llm-pretraining-optimization`. Does **not** replace Muon2.

## Gotchas & Failure Modes
- GitHub repo is dualverse-ai/chorous (typo).
- Ember is table-optimizer memory, not a Muon2 replacement.
