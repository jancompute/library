---
id: method:statealign
type: method
title: StateAlign
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'variable environment latency / async stragglers'
    reason: 'SAO remains async straggler replay; StateAlign is state-contrast credit for multi-turn tool hallucination'
    use_instead: method:sao
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift or rubric credit)'
    reason: 'CANOPY remains AppWorld coverage; StateAlign is BFCL-v4 tool-state contrast, not a coverage kernel'
    use_instead: method:canopy
  - when: 'decision-plane RL for executable actions (RLiD), not async stragglers'
    reason: 'RLiD is decision-plane RL; StateAlign contrasts tool-call vs ask/wait states'
    use_instead: method:rlid
assumptions:
  - 'Multi-turn tool agents with inspectable task state (available info, tool capability, progress). Paper: Qwen3-8B BFCL v4. Code ZhexiLu/StateAlign as of 2026-11-13.'
last_reviewed: '2026-11-13'
papers:
- paper:statealign
recipes:
- recipe:statealign
claims:
- benchmark: 'Qwen3-8B BFCL v4 multi-turn; no-tool hallucination vs outcome-only'
  metric: 'multi-turn accuracy; hallucination rate'
  value: '45.5%→55.2% multi-turn; no-tool hallucination 62.2%→56.1% vs outcome-only'
  baseline: 'outcome-only RL'
  date: '2026-11-13'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.16304'
  notes: 'Does not retarget method:sao or method:canopy. Distinct from method:rlid. Code ZhexiLu/StateAlign released. Mention on task:outcome-only-long-horizon-agent-rl.'
tags:
- agentic-rl
- tool-use
- state-contrast
- active
---

# StateAlign

## Method Overview
StateAlign is state-contrast RL for multi-turn tool agents. The update contrasts the current task state (available information, tool capability, progress) against a counterfactual so the policy learns when to call, ask, or wait. Outcome-only RL can raise task reward while increasing tool hallucination; state contrast cuts that on BFCL v4.

## When to Use
- Multi-turn tool RL where outcome reward and tool hallucination move together, and the interaction state is inspectable.

## When NOT to Use
Async stragglers remain `method:sao`. AppWorld coverage remains `method:canopy`. Decision-plane executable actions remain `method:rlid`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:agentic-async-rl`. Mention on `task:outcome-only-long-horizon-agent-rl`. Does **not** replace SAO or CANOPY.

## Gotchas & Failure Modes
- Needs a state descriptor; outcome-only groups without state labels cannot form the contrast.
- Not a coverage kernel and not an async straggler replay.
