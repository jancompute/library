---
id: method:muted-distillation
type: method
title: Muted Distillation
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'action-only distill with empty think block / CoT-proxies (CoT-Proxy; not ActionOPD / not Muted Distillation)'
    reason: 'Muted Distillation hides student thoughts from a live OPD teacher; CoT-Proxy is action-only SFT with an empty think block'
    use_instead: method:cot-proxy
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains the matching default; muted distillation hides thought tokens from the teacher'
    use_instead: method:opd
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift or rubric credit)'
    reason: 'CANOPY remains coverage RL; muted distillation is an OPD length-inflation fix, not sparse-outcome RL'
    use_instead: method:canopy
  - when: 'length-scaling tax under RLVR; route solved prompts to EMA OPD'
    reason: 'LSD routes solved GRPO groups to EMA OPD; muted distillation mutes student thoughts in the teacher context'
    use_instead: method:lsd
  - when: 'OPD EOS termination gotcha / semantic-class stop'
    reason: 'OPD-EOS is stop-id mismatch; muted distillation is thought-token hiding'
    use_instead: method:opd-eos
assumptions:
  - 'Qwen3.5 4B/9B/27B. OfficeQA Pro and SpreadsheetBench. Teacher sees an empty thinking block; reverse-KL on visible tail only. Few lines, no extra HPs. No public code as of 2026-11-24.'
last_reviewed: '2026-11-24'
papers:
- paper:muted-distillation
recipes:
- recipe:muted-distillation
claims:
- benchmark: 'OfficeQA Pro / SpreadsheetBench vs OPD, Qwen3.5 family'
  metric: 'output tokens per episode; SpreadsheetBench pass@1'
  value: 'tokens −57% / −53% vs OPD; SpreadsheetBench pass@1 +4.8; matches OPD accuracy on OfficeQA Pro'
  baseline: 'vanilla reverse-KL OPD'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.28445'
  notes: 'Student becomes more concise than the untrained base. No extra data or hyperparameters. No public GitHub. Does not retarget OPD or CANOPY.'
tags:
- distillation
- opd
- token-efficiency
- agents
- active
---

# Muted Distillation

## Method Overview
Muted Distillation hides the student's thought tokens from the OPD teacher (empty thinking block) and applies reverse-KL only on the visible tail. Standard OPD inflates per-turn reasoning because the teacher extends partial thoughts. Few lines of context masking; no extra hyperparameters.

## When to Use
- Multi-turn agentic OPD when thought traces dominate the teacher context and output length inflates.

## When NOT to Use
Matching default remains `method:opd`. Sparse-outcome agent RL remains `method:canopy`. Stop-id mismatch remains `method:opd-eos`. Length-scaling tax mix remains `method:lsd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Mention on `task:outcome-only-long-horizon-agent-rl`. Distinct from OPD, OPD-EOS, LSD. Does **not** replace OPD or CANOPY.

## Gotchas & Failure Modes
- No public code at ingest (`code_status: none`).
- Teacher never sees student thoughts; if the student must copy teacher CoT style, mute will hurt.
- Reported on OfficeQA Pro / SpreadsheetBench, not math Pass@1.
