---
id: method:cot-proxy
type: method
title: CoT-Proxy
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains reverse-KL matching; CoT-Proxy is action-only SFT with an empty think block plus optional short proxies'
    use_instead: method:opd
  - when: 'action-level OPD without teacher token probabilities'
    reason: 'ActionOPD is action-level OPD; CoT-Proxy is SFT on teacher actions with empty think plus KL replay to the initial student'
    use_instead: method:actionopd
  - when: 'hide student thoughts from the OPD teacher / tail-only reverse-KL (Muted Distillation; not OPD-EOS)'
    reason: 'Muted Distillation hides student thoughts from a live OPD teacher; CoT-Proxy never sees teacher CoT'
    use_instead: method:muted-distillation
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift or rubric credit)'
    reason: 'CANOPY remains coverage RL; CoT-Proxy is teacher-action distill, not sparse-outcome grouping'
    use_instead: method:canopy
assumptions:
  - 'Student chat template with an empty reasoning block. KL replay to the initial student on its own generations. Optional short CoT-proxies after the empty block. Closed-teacher path uses visible actions plus API reasoning summaries. No public code as of 2026-11-25.'
last_reviewed: '2026-11-25'
papers:
- paper:cot-proxy
recipes:
- recipe:cot-proxy
claims:
- benchmark: 'Qwen3-4B / 32B AppWorld vs untrained, action-only then CoT-proxy'
  metric: 'task success'
  value: 'Qwen3-4B 7%→18% action-only / 35% with CoT-proxy; Qwen3-32B 12%→25% action-only'
  baseline: 'untrained student; full-CoT SFT when teacher CoT is visible'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.33148'
  notes: 'Empty-think SFT transfers to inference with thinking on (cross-format transfer). Teacher is Qwen3.6-27B. No public GitHub.'
- benchmark: 'Qwen3-4B distilled from GPT-5.6 Luna visible outputs + API summaries'
  metric: 'AppWorld / SWE-bench Verified task success'
  value: 'AppWorld 7%→48%; SWE-bench Verified 3%→28%'
  baseline: 'untrained Qwen3-4B'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.33148'
  notes: 'Closed-teacher path never needs hidden CoT. SWE-Verified 28% is distill transfer, not a harness ranking. Does not retarget OPD or CANOPY.'
tags:
- distillation
- agents
- sft
- active
---

# CoT-Proxy

## Method Overview
Train the student on teacher actions with an empty reasoning block, plus a KL replay buffer of the student's own generations against the initial checkpoint. Optional CoT-proxies are short summaries placed after the empty block. The empty-think policy transfers to inference with thinking enabled (cross-format transfer) and works when the teacher hides CoT.

## When to Use
- Distilling a long-horizon agent from a stronger teacher whose chain-of-thought is hidden, or when imitating full CoT is too expensive.

## When NOT to Use
Live reverse-KL matching remains `method:opd`. Action-level OPD remains `method:actionopd`. Thought-hiding OPD remains `method:muted-distillation`. Sparse-outcome coverage remains `method:canopy`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Mention on `task:outcome-only-long-horizon-agent-rl`. Distinct from ActionOPD, Muted Distillation, AutoMaster, COPD. Does **not** replace OPD or CANOPY.

## Gotchas & Failure Modes
- No public code at ingest (`code_status: none`).
- Drop the KL replay and the student drifts from its initial assistant.
- SWE-bench Verified 28% is closed-teacher distill transfer, not a mini-SWE-agent ranking.
