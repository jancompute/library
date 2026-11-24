---
id: method:contrastive-opd
type: method
title: cOPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains the matching default; cOPD needs a strong teacher and a weak teacher'
    use_instead: method:opd
  - when: 'black-box NL consult then privileged OPSD+RL (COPD; not matching default / not ActionOPD)'
    reason: 'method:copd is communicative OPD; this node is contrastive dual-branch OPD'
    use_instead: method:copd
  - when: 'multi-teacher Open-MOPD token-share balancing'
    reason: 'Open-MOPD is the multi-teacher default; cOPD is a dual-branch contrast, not token-share MOPD'
    use_instead: method:open-mopd
  - when: 'weak-to-strong reverse distillation (OPRD)'
    reason: 'OPRD amplifies student gradients along the teacher policy-shift; cOPD contrasts two teachers at student prefixes'
    use_instead: method:oprd
assumptions:
  - 'Qwen3-4B student with 0.6B/1.7B weak teachers; Llama-3.2-3B with 1B weak teacher. Strong teachers: Qwen3-32B / Llama-3.1-8B. Top-16, mask margin δ, tanh(Δ/τ). JustRL and IF / abstention QA. MUST NOT reuse slug copd. No public code as of 2026-11-24.'
last_reviewed: '2026-11-24'
papers:
- paper:contrastive-opd
recipes:
- recipe:contrastive-opd
claims:
- benchmark: 'JustRL config pooled math Pass@16 vs JSD / strong teacher'
  metric: 'Pass@16'
  value: '77.46 vs JSD 75.14 / RKL 73.89 / W2S-OPD 71.27 / strong teacher 75.72'
  baseline: 'JSD; reverse-KL OPD; W2S-OPD; strong teacher'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.28359'
  notes: 'Abstract "up to 7.51%" is vs W2S-OPD on Qwen3 4B/0.6B/1.7B (65.32 vs 57.80), not vs JSD on JustRL. No public GitHub.'
- benchmark: 'Qwen3 4B/0.6B/1.7B math Pass@16 vs W2S-OPD'
  metric: 'Pass@16'
  value: '65.32 vs W2S-OPD 57.80 / JSD 62.76; matches strong teacher 65.32'
  baseline: 'W2S-OPD; JSD; strong teacher'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.28359'
  notes: '+7.52 vs W2S-OPD. IF Qwen3 24.26 vs RKL +0.80; Llama 21.73 vs W2S-OPD +1.96. QA abstention Qwen3 71.59 / Llama 73.04.'
tags:
- distillation
- opd
- contrastive
- multi-teacher
- active
---

# cOPD

## Method Overview
cOPD scores student prefixes against a strong teacher, a weak teacher, and the student. Dual-branch Top-16 masks keep tokens where the student sits a margin below the strong teacher and above the weak teacher. The update is a \(\tanh(\Delta_v/\tau)\) log-odds contrast. MUST NOT reuse slug `copd` (`method:copd` is black-box communicative OPD).

## When to Use
- On-policy distillation when a weaker same-family checkpoint is available as a contrastive reference, not only as a worse imitation target.

## When NOT to Use
Matching default remains `method:opd`. Communicative COPD remains `method:copd`. Multi-teacher token-share remains `method:open-mopd`. Reverse distillation remains `method:oprd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Distinct from OPD, COPD, Open-MOPD, W2S-OPD, OPRD. Does **not** replace OPD.

## Gotchas & Failure Modes
- No public code at ingest (`code_status: none`).
- Headline 7.51% is vs W2S-OPD on one Qwen3 config, not vs JSD on JustRL.
- Needs two teachers plus student logits; not a single-teacher sampled-token overlay.
