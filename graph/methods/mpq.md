---
id: method:mpq
type: method
title: 'MPQ'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:full-lowbit-finetune'
  reason: 'GradCodeS remains deployed low-bit FT; MPQ is PTQ that delays codeword commit via message passing'
  use_instead: method:gradcodes
assumptions:
- 'PTQ without retraining. Code poseidonchan/MPQ.'
last_reviewed: '2026-10-26'
papers:
- paper:mpq
recipes:
- recipe:mpq
claims:
- benchmark: 'PTQ vs GPTQ / LDLQ / block coordinate descent that commits each block early'
  metric: 'low-bit PTQ quality after delayed codeword assignment'
  value: 'message-passing PTQ that keeps near-optimal codewords in play instead of committing each block first'
  baseline: 'GPTQ; LDLQ; block coordinate descent PTQ'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32127'
  notes: 'Does not retarget method:gradcodes.'
tags:
- quantization
- ptq
- active
---

# MPQ

## Method Overview
MPQ casts PTQ as message passing so a weight block is not committed to one codeword before its neighbors are seen.

## When to Use
- PTQ of an existing LLM when GPTQ-style early commit leaves better codewords on the table.

## When NOT to Use
Default on `task:full-lowbit-finetune` remains `method:gradcodes`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:gradcodes`.

## Gotchas & Failure Modes
- Not a replacement for `method:gradcodes`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
