---
id: method:swe-opd
type: method
title: SWE-OPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains the matching default; SWE-OPD is agentic-coding OPD with an offline cached teacher'
    use_instead: method:opd
  - when: 'cross-tokenizer OPD (strict 1:1 coverage / student-selected top-16 shared-vocab reverse-KL)'
    reason: 'Cross-Tokenizer OPD owns the 1:1 / k=16 bake-off; SWE-OPD reports a SWE-bench Pro transfer, not that protocol'
    use_instead: method:cross-tokenizer-opd
  - when: 'GitHub issue to patch / SWE harness'
    reason: 'mini-SWE-agent remains the issue-to-patch loop; SWE-OPD is post-train distill of a coding agent'
    use_instead: method:mini-swe-agent
  - when: 'multi-turn agent OPD at pivotal early mistakes'
    reason: 'PivotOPD is prevent+recover at pivotal turns; SWE-OPD is SWE-bench Pro OPD with a cached teacher'
    use_instead: method:pivotopd
assumptions:
  - 'Agentic coding traces. Offline cached teacher cuts GPU-hours. Cross-tokenizer GLM-4.5-Air from DeepSeek-V4-Flash is a transfer, not the library 1:1 bake-off. Decreasing top-K reverse-KL can still cause repetition (support-mass gradient). Code ernie-research/SWE-OPD.'
last_reviewed: '2026-11-17'
papers:
- paper:swe-opd
recipes:
- recipe:swe-opd
claims:
- benchmark: 'SWE-bench Pro / Multilingual; Qwen3.5-9B from Qwen3.6-27B; GLM-4.5-Air from DeepSeek-V4-Flash-0731; GPU-hours'
  metric: 'resolve rate; GPU-hours; peak GPU'
  value: 'Qwen3.5-9B SWE-bench Pro 35.9→39.4; offline cached teacher 59.4–72.6% fewer GPU-h and ~half peak GPU; GLM-4.5-Air 35.8→39.7 Pro / 41.8→46.2 Multilingual'
  baseline: 'student without SWE-OPD; live online teacher OPD'
  date: '2026-11-17'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.21020'
  notes: 'Does not retarget method:opd / method:cross-tokenizer-opd / method:mini-swe-agent. Decreasing loss is not a quality signal under top-K reverse-KL (repetition).'
tags:
- opd
- swe
- agent
- active
---

# SWE-OPD

## Method Overview
SWE-OPD is on-policy distillation for agentic coding. An offline cached teacher cuts end-to-end GPU-hours 59.4–72.6% and halves peak GPU versus live teacher sampling. The same offline path transfers across tokenizers (GLM-4.5-Air from DeepSeek-V4-Flash). A decreasing top-K reverse-KL loss can still produce severe repetition via a support-mass gradient term.

## When to Use
- Distilling a stronger coding agent into a smaller student on SWE-bench-style traces, especially when you can cache teacher logp.

## When NOT to Use
Matching default remains `method:opd`. Cross-tokenizer 1:1 remains `method:cross-tokenizer-opd`. Issue-to-patch harness remains `method:mini-swe-agent`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Mentions on `task:cross-tokenizer-opd` and `task:software-engineering-agent-harness`. Does **not** replace OPD, Cross-Tokenizer OPD, or mini-SWE-agent.

## Gotchas & Failure Modes
- Decreasing top-K reverse-KL is not a resolve-rate signal; watch repetition.
- Paper GLM/DeepSeek numbers are not the library 1:1 / k=16 bake-off.
