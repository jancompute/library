---
id: method:copd
type: method
title: COPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains logit matching; COPD consults a black-box teacher in natural language then privileged OPSD'
    use_instead: method:opd
  - when: 'action-level OPD without teacher token probabilities'
    reason: 'ActionOPD aligns semantic actions; COPD is NL consult then privileged OPSD+RL'
    use_instead: method:actionopd
  - when: 'black-box step queries then SFT when the teacher hides CoT'
    reason: 'Stepwise Querying queries then SFT; COPD is student-initiated consult plus OPSD+RL'
    use_instead: method:stepwise-querying
  - when: 'trace-bridged self-distillation when teacher logp is missing'
    reason: 'Bridged Self-Distill is a missing-logp self-teacher; COPD consults a live black-box teacher'
    use_instead: method:bridged-self-distill
  - when: 'file-based coding-agent memory via async OPD (CAMP-II; not write-time playbook)'
    reason: 'CAMP-II is file-as-memory OPD; COPD is communicative black-box distill on CAMG-II'
    use_instead: method:camp-ii
  - when: 'outcome-only AppWorld coverage / anti-drift'
    reason: 'CANOPY remains sparse-outcome coverage; COPD is black-box teacher distill'
    use_instead: method:canopy
assumptions:
  - 'Black-box teacher with no logits. Student-initiated NL consult during task execution. Privileged OPSD on adviser-free rollouts plus task-reward RL. Paper: Qwen3.5-4B/9B on CAMG-II, TB 2.1, SWE-Bench Pro V2. Distinct slug from cisnlp/COPSD. No public train code as of 2026-11-19.'
last_reviewed: '2026-11-19'
papers:
- paper:copd
recipes:
- recipe:copd
claims:
- benchmark: 'CAMG-II adviser-free (Qwen3.5-4B/9B vs ActionOPD)'
  metric: 'equal-weight domain avg'
  value: '4B 45.3→59.8 vs ActionOPD 51.2 (2.46× gain); 9B 54.2→61.3 vs ActionOPD 54.6'
  baseline: 'Init / ActionOPD'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.23673'
  notes: 'Does not retarget method:opd / method:canopy. Distinct from method:actionopd / method:bridged-self-distill / method:stepwise-querying / method:camp-ii. code_status none.'
- benchmark: 'Terminal-Bench 2.1 / SWE-Bench Pro V2 (COPD-4B/9B, no adviser)'
  metric: 'resolution rate'
  value: '4B 23.1/11.2→28.0/16.5; 9B 23.1/23.1→33.0/27.5 (avg 30.3 vs Qwen3.5-35B-A3B 30.6)'
  baseline: 'Qwen3.5-4B/9B init'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.23673'
  notes: 'Transfer, not a SWE harness ranking. Does not retarget method:mini-swe-agent.'
tags:
- opd
- black-box
- agentic
- camg-ii
- active
---

# COPD

## Method Overview
Communicative On-Policy Distillation (COPD) lets a student consult a black-box teacher in open-ended natural language during task execution. Successful consultations become privileged references that supervise adviser-free student rollouts via on-policy self-distillation, jointly with task-reward RL.

## When to Use
- Distill a stronger teacher that exposes only text, not logits, into a long-horizon agent student.

## When NOT to Use
Matching distillation remains `method:opd`. Action-level no-logp OPD remains `method:actionopd`. Black-box step-query SFT remains `method:stepwise-querying`. Missing-logp self-teachers remain `method:bridged-self-distill`. File-as-memory OPD remains `method:camp-ii`. AppWorld coverage remains `method:canopy`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Mention on `task:outcome-only-long-horizon-agent-rl`. Does **not** replace OPD or CANOPY.

## Gotchas & Failure Modes
- Distinct from cisnlp/COPSD (crosslingual).
- Test is adviser-free; communication is a train-time privilege.
- No public train code (`code_status: none`; project page only).
