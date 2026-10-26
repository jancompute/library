---
id: method:alto-mxfp4
type: method
title: 'ALTO MXFP4'
category: quantization
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:fp4-hardware-training'
  reason: 'Quartet-II / MXFP4 remain native FP4 hardware SOTA; ALTO is a GPT-OSS-20B MXFP4 recipe on MLPerf Small MoE'
  use_instead: method:quartet-ii
assumptions:
- 'GPT-OSS-20B MXFP4 on MLPerf Small MoE. AMD/OLMo-adjacent recipe.'
last_reviewed: '2026-10-26'
papers:
- paper:alto-mxfp4
recipes:
- recipe:alto-mxfp4
claims:
- benchmark: 'GPT-OSS-20B MLPerf Small MoE MXFP4 vs BF16'
  metric: 'MXFP4 train quality gap to BF16'
  value: 'open MXFP4 recipe that closes the reported gap to BF16 on GPT-OSS-20B Small MoE'
  baseline: 'BF16 MoE train; unstabilized MXFP4'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32229'
  notes: 'Does not retarget method:quartet-ii.'
tags:
- quantization
- mxfp4
- active
---

# ALTO MXFP4

## Method Overview
ALTO is an open MXFP4 training recipe for GPT-OSS-20B that targets the BF16 quality gap on MLPerf Small MoE.

## When to Use
- MXFP4 MoE pretrain where naive FP4 noise destabilizes the run.

## When NOT to Use
Default on `task:fp4-hardware-training` remains `method:quartet-ii`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:quartet-ii`.

## Gotchas & Failure Modes
- Not a replacement for `method:quartet-ii`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
