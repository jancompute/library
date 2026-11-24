---
id: method:aprm
type: method
title: APRM
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; APRM is a ~46M attention process RM mixed into GRPO/GPG/DAPO'
    use_instead: method:cispo
  - when: 'all-zero verifier groups / process supervision from outcome-only RL (TIPS)'
    reason: 'TIPS is an outcome-trained generative PRM; APRM is an attention process RM'
    use_instead: method:tips
  - when: 'verifier-grounded trajectory-balance self-improvement'
    reason: 'FlowBalance is trajectory-balance self-guidance; APRM is an attention process score'
    use_instead: method:flowbalance
  - when: 'SAE-guided token credit on GRPO/GSPO (SAEPO)'
    reason: 'SAEPO is SAE feature contrast; APRM is a learned attention process RM'
    use_instead: method:saepo
assumptions:
  - 'Qwen3-1.7B/4B-Base GRPO/GPG; Qwen3.5-2B DAPO. ~46M APRM, β=0.3 process mix, ranking+counterfactual, periodic refresh. Shuffle drops ranking 78.55→62.54 (1.7B). No public code as of 2026-11-24.'
last_reviewed: '2026-11-24'
papers:
- paper:aprm
recipes:
- recipe:aprm
claims:
- benchmark: 'Qwen3-1.7B/4B-Base GRPO pass@8 vs GRPO; GPG+APRM'
  metric: 'pass@8; 4B GPG avg@8 / pass@8'
  value: '1.7B GRPO 52.62→55.97, GPG+APRM 58.13; 4B GRPO 61.68→65.06; GPG+APRM avg@8 47.02 / pass@8 65.84'
  baseline: 'GRPO; GPG'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.30627'
  notes: 'Average pass@8 +2.88% across reported hosts. Distinct from TIPS / VeriGate / CISPO. No public GitHub.'
- benchmark: 'Qwen3.5-2B DAPO+APRM math / code vs DAPO'
  metric: 'avg@8 / pass@8 deltas'
  value: 'math +1.34 / +4.78; code +1.64 / +2.96'
  baseline: 'DAPO'
  date: '2026-11-24'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.30627'
  notes: 'GPG 4B median length −17.08%. Shuffle ranking 78.55→62.54 at 1.7B. Does not retarget CISPO.'
tags:
- rlvr
- process-reward
- attention
- credit-assignment
- active
---

# APRM

## Method Overview
APRM is a ~46M-parameter process reward on hidden states and attention maps. Ranking plus counterfactual attention shuffle trains it. The score mixes into GRPO/GPG/DAPO advantages at \(\beta=0.3\) and is refreshed during RL. Distinct from textual PRMs and TIPS.

## When to Use
- Dense math/code RLVR when a cheap process RM on attention maps can reshape group advantages without a textual PRM.

## When NOT to Use
Pass@1 remains `method:cispo`. Outcome-trained generative PRM remains `method:tips`. SAE token contrast remains `method:saepo`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:math-code-rl-dense`. Distinct from CISPO, TIPS, VeriGate, SAEPO. Does **not** replace CISPO.

## Gotchas & Failure Modes
- No public code at ingest (`code_status: none`).
- Needs hidden states and attention maps; not a verifier-only overlay.
- Counterfactual shuffle is the sanity check: ranking should drop (78.55→62.54 at 1.7B).
