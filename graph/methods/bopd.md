---
id: method:bopd
type: method
title: 'BOPD (Bootstrapped On-Policy Distillation)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
    - when: 'privileged-teacher OPSD with a gold reference (VISTA default)'
      reason: 'VISTA stays the privileged-teacher first hop; BOPD retires the privileged teacher after Stage I'
      use_instead: method:vista
    - when: 'same-tokenizer single-teacher matching distillation'
      reason: 'OPD remains matching; BOPD is a two-stage OPSD then OPD bootstrap'
      use_instead: method:opd
    - when: 'prepare-then-freeze teacher RL on student prefixes'
      reason: 'Prep-OPD RL-trains an external teacher then freezes; BOPD bootstraps a same-size OPSD teacher'
      use_instead: method:prep-opd
assumptions:
    - 'Same-size privileged OPSD teacher in Stage I, then a fresh student from the initial checkpoint in Stage II. Paper: Qwen3-4B/8B and SmolLM3-3B, LoRA r=64, 100 steps/stage. Code YueWu0301/BOPD. arXiv 2611.13680 above watermark 2611.12886.'
last_reviewed: '2026-11-11'
papers:
- paper:bopd
recipes:
- recipe:bopd
claims:
- benchmark: 'Qwen3-4B/8B AIME24/AIME25/HMMT25 Avg@12 / Pass@12'
  metric: 'mean Avg@12 vs initial / OPSD teacher'
  value: '4B 23.98 vs initial 18.06 / OPSD 19.63; 8B 22.04 vs 18.70 / 20.19; Pass@12 4B 54.44 vs 42.22 / 46.67'
  baseline: 'initial model / continued OPSD (Stage I teacher)'
  date: '2026-11-11'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.13680'
  notes: 'Does not retarget method:vista or method:opd. Overlap@16 rises under BOPD (0.8638→0.9005) and falls under continued OPSD (0.8930→0.8272).'
tags:
- distillation
- opsd
- opd
- bootstrap
- active
---

# BOPD (Bootstrapped On-Policy Distillation)

## Method Overview
BOPD splits privileged OPSD from student OPD. Stage I trains an OPSD student against a frozen reference-conditioned copy of the initial model. Stage II discards that student as a policy and uses it as a reference-free teacher for a fresh copy of the initial model. Continued OPSD degrades as the privileged teacher and the reference-free student diverge.

## When to Use
- Privileged gold solutions exist, but prolonged OPSD starts to reverse early gains.

## When NOT to Use
Privileged-teacher default remains `method:vista`. Single-teacher matching remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:privileged-teacher-opsd`. Mention on `task:student-distillation`. Does **not** replace VISTA or OPD.

## Gotchas & Failure Modes
- Two full stages (100 steps each in the paper). Do not keep training the Stage I student as the deployable policy.
- Code generation gains are smaller than math (4B mean 46.54 vs OPSD 45.53).
- Sibling of Prep-OPD / RetireOPD / DCE+SRCL, not a replacement.
