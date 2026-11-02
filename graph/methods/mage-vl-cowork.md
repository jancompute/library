---
id: method:mage-vl-cowork
type: method
title: 'Mage-VL-Cowork'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'hybrid GUI+code recreation train/eval (RecreationWorld)'
  reason: 'RecreationWorld remains the hybrid CUA first hop; Mage is a 4B five-stage trained policy'
  use_instead: method:recreationworld
- when: 'desktop/OS GUI ranking on OSWorld 2.0 paper protocol'
  reason: 'OSWorld-Verified is not the locked ranking protocol'
  use_instead: method:claude-computer-use
- when: 'native GUI+code CUA trained with step-balanced GSPO (OS-Helix)'
  reason: 'OS-Helix is the other trained hybrid CUA sibling; Mage is a 4B evolved-harness recipe'
  use_instead: method:os-helix
assumptions:
- 'Hybrid GUI+code CUA that must be trained. Paper: 4B. Code microsoft/Mage.'
last_reviewed: '2026-11-02'
papers:
- paper:mage-vl-cowork
recipes:
- recipe:mage-vl-cowork
claims:
- benchmark: 'OSWorld-Verified (NOT OSWorld 2.0)'
  metric: 'success at 4B after five-stage curriculum'
  value: '66.0%'
  baseline: 'untrained / earlier Mage stages; OS-Helix 27B-RL 66.44% is a different scale'
  date: '2026-11-02'
  verified: false
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.40747'
  notes: 'Does not demote method:claude-computer-use. Does not replace method:recreationworld. Distinct from method:os-helix.'
tags:
- computer-use
- hybrid
- active
---

# Mage-VL-Cowork

## Method Overview
Mage-VL-Cowork trains a 4B hybrid CUA through a five-stage midtraining/SFT/RL curriculum on tasks synthesized by Mage-CUA-Forge, evolving teacher harnesses instead of distilling a default teacher.

## When to Use
- Training a small on-device hybrid GUI+code CUA from a multimodally aligned checkpoint.

## When NOT to Use
RecreationWorld remains the hybrid CUA train/eval first hop. Claude computer-use remains OSWorld 2.0 ranking.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:recreationworld` or `method:claude-computer-use`. Sibling of `method:os-helix`.

## Gotchas & Failure Modes
- OSWorld-Verified is not OSWorld 2.0 paper protocol.
- Paper claims are preprint-dated 2026-11-02; no locked-SOTA bake-off.
