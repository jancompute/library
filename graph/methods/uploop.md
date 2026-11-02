---
id: method:uploop
type: method
title: 'UpLoop'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the first hop on task:elastic-depth-looped-lm'
  reason: 'ELR remains mixed-depth elastic recurrence; UpLoop is a FLOP-matched dense upcycling schedule'
  use_instead: method:elr
- when: 'compute-matched MoE looping of middle layers (FLOPs/params/KV matched)'
  reason: 'SMELT remains MoE layer looping; UpLoop is dense progressive-depth copy'
  use_instead: method:smelt
- when: 'Huginn-style dense fixed-point looping with terminal KV sharing'
  reason: 'Looped Models Done Right remains Huginn looping; UpLoop is an upcycling schedule'
  use_instead: method:looped-models-done-right
assumptions:
- 'Dense looped Transformer pretrain matched on params, tokens, and train FLOPs. No public code as of 2026-11-02.'
last_reviewed: '2026-11-02'
papers:
- paper:uploop
- paper:no-free-loop
recipes:
- recipe:uploop
claims:
- benchmark: '1.3B dense looped pretrain, 22 downstream tasks vs matched dense baseline'
  metric: 'average score'
  value: '22.99 to 27.52'
  baseline: 'matched-params/tokens/FLOPs dense Transformer; ELR / SMELT / Huginn not the paper bake-off'
  date: '2026-11-02'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.41720'
  notes: 'Does not retarget method:elr. Mention on task:compute-matched-moe-looped-pretrain.'
tags:
- pretraining
- looped-lm
- active
---

# UpLoop

## Method Overview
UpLoop upcycles a dense Transformer into a looped model at no extra pretrain compute: start shallow, copy learned layers to grow depth, then spend the saved early FLOPs on repeated execution of a shared middle block.

## When to Use
- You want looped-Transformer gains under a matched dense pretrain FLOP/param/token budget, not mixed-depth serving.

## When NOT to Use
ELR remains mixed-depth elastic recurrence. SMELT remains compute-matched MoE looping. Huginn-style looping remains Looped Models Done Right. Post-train loops on a finished checkpoint are `paper:no-free-loop`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:elr`, `method:smelt`, or `method:looped-models-done-right`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-11-02; no locked-SOTA bake-off.
- No public code as of 2026-11-02.
- Post-train loops on already-pretrained 4B/9B models fail the equal-parameter test (`paper:no-free-loop`).
