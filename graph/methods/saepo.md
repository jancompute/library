---
id: method:saepo
type: method
title: SAEPO
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; SAEPO is SAE-guided token credit on GRPO/GSPO'
    use_instead: method:cispo
  - when: 'RLVR token-filter plug-in keeping top-20% tokens by |E·ω| on GRPO/DAPO/CISPO-family trainers'
    reason: 'GMTS ranks tokens by |entropy × advantage|; SAEPO contrasts SAE features of correct vs incorrect groups'
    use_instead: method:gmts
  - when: 'entropy-rank token keep-mask on DAPO/GRPO (CreditFilter; not GMTS |E·ω|)'
    reason: 'CreditFilter is a within-response entropy-rank window; SAEPO is SAE feature contrast'
    use_instead: method:creditfilter
  - when: 'attention process RM mixed into GRPO/GPG/DAPO (APRM)'
    reason: 'APRM is a learned attention process RM; SAEPO is a frozen SAE credit overlay'
    use_instead: method:aprm
assumptions:
  - 'Qwen3-1.7B/4B-Base GRPO/GSPO; OLMo-3-7B-Base. Frozen SAE, train-only. Silent groups get no SAE signal. No public code as of 2026-11-24.'
last_reviewed: '2026-11-24'
papers:
- paper:saepo
recipes:
- recipe:saepo
claims:
- benchmark: 'Qwen3-1.7B-Base GRPO/GSPO math avg vs host'
  metric: 'math avg'
  value: 'GRPO 35.56→38.68; GSPO 36.63→39.55'
  baseline: 'GRPO; GSPO; KTAE; THR; GTPO'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.29936'
  notes: 'Abstract ceiling +6.63 math / +5.57 code. Silent groups get no SAE signal. Distinct from GMTS / CreditFilter / APRM. No public GitHub.'
- benchmark: 'Qwen3-4B-Base GRPO math / code avg vs GRPO'
  metric: 'math avg; code avg'
  value: 'math 48.43→49.97; code 12.11→17.68 (+5.57)'
  baseline: 'GRPO'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.29936'
  notes: 'Verifier, clip, and KL stay unchanged. SAE is train-only. Does not retarget CISPO.'
tags:
- rlvr
- sae
- credit-assignment
- grpo
- active
---

# SAEPO

## Method Overview
SAEPO reshapes GRPO/GSPO token advantages with a frozen SAE. Tokens similar to correct-group tokens of the same prompt get credit; tokens similar to incorrect-group tokens get penalized. Verifier, clip, and KL stay unchanged. The SAE is train-only.

## When to Use
- Critic-free math/code RLVR when mixed-correctness groups exist and a frozen SAE can separate correct vs incorrect tokens.

## When NOT to Use
Pass@1 remains `method:cispo`. Batch |E·ω| remains `method:gmts`. Within-response entropy-rank remains `method:creditfilter`. Attention process RM remains `method:aprm`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:math-code-rl-dense`. Distinct from CISPO, GMTS, CreditFilter, APRM. Does **not** replace CISPO.

## Gotchas & Failure Modes
- No public code at ingest (`code_status: none`).
- All-fail / all-pass groups have no SAE contrast; pair with VeriGate / GRAFT if silent groups dominate.
- SAE is train-only; do not ship it at inference.
