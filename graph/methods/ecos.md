---
id: method:ecos
type: method
title: 'ECOS (Environment-Calibrated OPSD)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'outcome-only long-horizon agent RL (AppWorld coverage / anti-drift)'
  reason: 'CANOPY remains sparse-outcome coverage; ECOS is command-only privileged OPSD'
  use_instead: method:canopy
- when: 'privileged-teacher OPSD / gold-solution self-distillation'
  reason: 'VISTA remains text-math privileged OPSD; ECOS is agent command-only teacher'
  use_instead: method:vista
- when: 'choosing the single-teacher distillation algorithm'
  reason: 'OPD remains matching; ECOS is environment-calibrated agent OPSD'
  use_instead: method:opd
assumptions:
- 'Multi-turn agent traces with an executable command channel. Paper: Qwen2.5-3B/7B ALFWorld/WebShop. Teacher sees command plus a one-token env-calibration suffix, not the full privileged response. No public code as of 2026-11-10. arXiv 2611.12232 above watermark 2611.09634.'
last_reviewed: '2026-11-10'
papers:
- paper:ecos
recipes:
- recipe:ecos
claims:
- benchmark: 'ALFWorld/WebShop Qwen2.5-3B/7B (seen / unseen)'
  metric: 'success vs GRPO; command-only vs full-response teacher'
  value: 'seen ALFWorld 90.5/93.3, WebShop 75.5/80.5; unseen ALFWorld +11.0/+7.6 vs GRPO; 3B WebShop command-only 75.0 vs full-response 52.3'
  baseline: 'GRPO / full-response OPSD teacher'
  date: '2026-11-10'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.12232'
  notes: 'Does not retarget method:canopy or method:vista.'
tags:
- distillation
- opsd
- agentic
- environment-calibration
- active
---

# ECOS (Environment-Calibrated OPSD)

## Method Overview
ECOS runs OPSD with a command-only teacher. The teacher sees the executable action plus a one-token environment-calibration suffix; it does not see the full privileged response.

## When to Use
- Agent OPSD that collapsed when the teacher saw full privileged traces.

## When NOT to Use
AppWorld coverage remains `method:canopy`. Text-math privileged OPSD remains `method:vista`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:outcome-only-long-horizon-agent-rl` with a mention on `task:privileged-teacher-opsd`. Does **not** replace CANOPY or VISTA.

## Gotchas & Failure Modes
- Full-response teacher is the failure mode the paper measures ($52.3$ vs $75.0$ on 3B WebShop).
- No public trainer.
- Not an AppWorld TGC ranking.
