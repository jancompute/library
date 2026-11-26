---
id: method:splice
type: method
title: SPLICE
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift or rubric credit)'
    reason: 'CANOPY remains coverage default; SPLICE salvages all-fail GRPO groups'
    use_instead: method:canopy
  - when: 'multi-model / all-fail group salvage by peer trajectory exchange'
    reason: 'GRAFT swaps peer traces; SPLICE splices bounded options at a branch point'
    use_instead: method:graft
  - when: 'sibling-harness rescue of all-fail GRPO groups (Harness-S; not the production kernel)'
    reason: 'Harness-S re-rolls the same policy under sibling harnesses; SPLICE splices options into learner continuations'
    use_instead: method:harness-s
  - when: 'policy-compatible joint decoding when all rollouts fail (PICO)'
    reason: 'PICO jointly decodes with an expert; SPLICE is a splice-then-continue local target'
    use_instead: method:pico
  - when: 'gating process supervision when verifier groups are silent'
    reason: 'VeriGate is the process-supervision gate; SPLICE is a group-salvage trainer'
    use_instead: method:verigate
  - when: 'variable environment latency / async stragglers, not sparse-outcome coverage'
    reason: 'SAO remains the async algorithm; SPLICE is all-fail salvage'
    use_instead: method:sao
assumptions:
  - 'All-fail GRPO groups. Frozen proposal splices bounded options at a branch point; learner-conditioned continuations; return-weighted local target. SWE-Verified and BrowseComp-Plus vs GRPO. Distinct from GRAFT / Harness-S / PICO / VeriGate. No public GitHub as of 2026-11-26.'
last_reviewed: '2026-11-26'
papers:
- paper:splice
recipes:
- recipe:splice
claims:
- benchmark: 'SWE-bench Verified and BrowseComp-Plus vs GRPO'
  metric: 'resolve / success pp; graduation on initially failed SWE'
  value: '+2.8–9.8pp vs GRPO; +10.8pp graduation on initially failed SWE'
  baseline: GRPO
  date: '2026-11-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34777'
  notes: 'Branch-point splice of bounded proposal options into learner continuations. Distinct from GRAFT / Harness-S / PICO / VeriGate. No public code. Does not retarget CANOPY, GRAFT, or VeriGate.'
tags:
- rl-alignment
- all-fail
- agentic
- active
---

# SPLICE

## Method Overview
SPLICE keeps a silent GRPO group instead of dropping it. A frozen proposal model inserts a bounded set of options at a branch point. The learner continues from those splices. The update is a return-weighted local target on the spliced segment, not a full trajectory swap.

## When to Use
- Long-horizon agent GRPO when groups go all-fail and you have a frozen proposal that can suggest bounded options at a branch point.

## When NOT to Use
Coverage default remains `method:canopy`. Peer-trajectory salvage remains `method:graft`. Sibling-harness rescue remains `method:harness-s`. Silent-group joint decoding remains `method:pico`. Process-supervision gating remains `method:verigate`. Async stragglers remain `method:sao`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:outcome-only-long-horizon-agent-rl` with mentions on `task:all-zero-verifier-groups` and `task:agentic-async-rl`. Distinct from GRAFT / Harness-S / PICO / VeriGate. Does **not** replace CANOPY, GRAFT, VeriGate, or SAO.

## Gotchas & Failure Modes
- No public GitHub as of 2026-11-26.
- The proposal is frozen; a weak proposal cannot invent a successful splice.
- Do not treat SWE-Verified transfer as a mini-SWE-agent harness ranking.
