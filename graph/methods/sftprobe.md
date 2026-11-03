---
id: method:sftprobe
type: method
title: 'SFTProbe'
category: data-curriculum
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:instruct-sft-alignment'
  reason: 'OLMo-3 remains the open instruct stack; SFTProbe is a data probe'
  use_instead: method:olmo-3
assumptions:
- 'Reasoning SFT traces. NeurIPS 2026. Project page only.'
last_reviewed: '2026-11-03'
papers:
- paper:sftprobe
recipes:
- recipe:sftprobe
claims:
- benchmark: 'mathematical reasoning SFT vs OpenThoughts-Math'
  metric: 'matched-pool accuracy / extra traces'
  value: '5k matches 89k OpenThoughts-Math; 7.5k +2.5%'
  baseline: 'generate-then-filter teacher pools; OpenThoughts-Math 89k'
  date: '2026-11-03'
  verified: true
  evidence_level: peer-reviewed
  source_url: 'https://arxiv.org/abs/2611.00554'
  notes: 'NeurIPS 2026. Does not retarget method:olmo-3.'
tags:
- sft
- data-selection
- active
---

# SFTProbe

## Method Overview
SFTProbe scores reasoning traces by probing a LoRA-adapted loss basin so difficulty and diversity come from compact loss signatures instead of extra teacher filters.

## When to Use
- Reasoning SFT data curation when generate-then-filter teacher pools take weeks.

## When NOT to Use
OLMo-3 remains the open instruct stack.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:olmo-3`.

## Gotchas & Failure Modes
- Project page only; no public GitHub as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
