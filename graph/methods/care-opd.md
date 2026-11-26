---
id: method:care-opd
type: method
title: CARE-OPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains the matching default; CARE-OPD is prefix-replay OPD for agent trajectories'
    use_instead: method:opd
  - when: 'OPD for agentic coding / offline cached teacher (SWE-OPD)'
    reason: 'SWE-OPD caches a frozen teacher; CARE-OPD completes student prefixes from replay'
    use_instead: method:swe-opd
  - when: 'multi-turn agent OPD at pivotal mistakes (prevent reverse-KL + recover forward-KL)'
    reason: 'PivotOPD edits at pivotal mistakes; CARE-OPD is prefix-replay plus confidence/hindsight allocation'
    use_instead: method:pivotopd
  - when: 'state-grounded on-policy distillation for multi-turn agents (matched interaction state, not student CoT)'
    reason: 'State-OPD matches interaction states; CARE-OPD is prefix-replay OPD'
    use_instead: method:state-opd
  - when: 'experience-calibrated OPD for multi-turn agents (ECOD; not matching default)'
    reason: 'ECOD reweights teachers; CARE-OPD allocates replay prefixes'
    use_instead: method:ecod
  - when: 'controllable tool-call efficiency / anchored reference budget (CARE-PO)'
    reason: 'CARE-PO is tool-budget RL; CARE-OPD is prefix-replay distillation. Do not reuse slug care-po.'
    use_instead: method:care-po
  - when: 'outcome-only long-horizon interactive agent RL'
    reason: 'CANOPY remains coverage default; CARE-OPD is a cheaper teacher for OPD'
    use_instead: method:canopy
assumptions:
  - 'Student prefixes stored in a replay buffer; a teacher completes them; confidence gating plus hindsight-return allocation. SWE-bench Verified vs async online OPD. Distinct from SWE-OPD / PivotOPD / State-OPD / ECOD / method:care-po. No public GitHub as of 2026-11-26.'
last_reviewed: '2026-11-26'
papers:
- paper:care-opd
recipes:
- recipe:care-opd
claims:
- benchmark: 'SWE-bench Verified, CARE-OPD vs async online OPD'
  metric: 'resolve rate; E2E time; env actions'
  value: '59.5%; −45% E2E time; −44% env actions'
  baseline: 'async online OPD'
  date: '2026-11-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34756'
  notes: 'Prefix-replay + confidence gating + hindsight allocation. Distinct from SWE-OPD / PivotOPD / State-OPD / ECOD / CARE-PO. No public code. Does not retarget OPD or CANOPY.'
tags:
- distillation
- opd
- agentic
- active
---

# CARE-OPD

## Method Overview
CARE-OPD keeps the OPD student update but drops live teacher rollouts. The student writes prefixes into a replay buffer. The teacher completes those prefixes. Completions are gated by teacher-student confidence and allocated by hindsight return so the budget goes to prefixes that still move the student.

## When to Use
- Agentic coding / long-horizon OPD where teacher rollouts dominate wall-clock and you can replay student prefixes.

## When NOT to Use
Matching default remains `method:opd`. Cached-teacher SWE distill remains `method:swe-opd`. Pivotal-mistake multi-turn OPD remains `method:pivotopd`. Tool-budget RL remains `method:care-po`. Coverage default remains `method:canopy`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation` with a mention on `task:outcome-only-long-horizon-agent-rl`. Distinct from SWE-OPD / PivotOPD / State-OPD / ECOD / CARE-PO. Does **not** replace OPD, Open-MOPD, or CANOPY.

## Gotchas & Failure Modes
- No public GitHub as of 2026-11-26.
- Prefix replay assumes the teacher can complete a student-seeded prefix; weak prefix coverage collapses to ordinary OPD cost.
- Do not confuse with `method:care-po` (tool-call budget).
