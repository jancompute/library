---
id: method:rlvb
type: method
title: RLVB
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift or rubric credit)'
    reason: 'CANOPY remains coverage RL when a programmatic checker exists; RLVB needs a simulator posterior over a hidden answer'
    use_instead: method:canopy
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; RLVB is commit-vs-continue credit from an evidence posterior'
    use_instead: method:cispo
  - when: 'variable environment latency / async stragglers'
    reason: 'SAO remains async tool RL; RLVB is a belief-backed outcome signal, not a straggler kernel'
    use_instead: method:sao
assumptions:
  - 'Simulator can compute the exact posterior over a hidden answer from gathered evidence. Reward never reads the agent-written belief line. Pro-Worlds plus two OOD benches, three VLMs. Code declare-lab/RLVB as of 2026-11-25.'
last_reviewed: '2026-11-25'
papers:
- paper:rlvb
recipes:
- recipe:rlvb
claims:
- benchmark: 'three VLMs × three benches vs base / GRPO / PPO / PPO+LLM-judge'
  metric: 'average relative gain; GPU-hours'
  value: '+17.1% vs base; +10.4% with EM; +9.3% vs PPO+LLM-judge at 1.6× fewer GPU-h. GRPO and PPO fall below base on average'
  baseline: 'untrained base; GRPO; PPO; PPO with an LLM-judge process reward'
  date: '2026-11-25'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.32884'
  notes: 'Sufficient-evidence answers 51%/12%/74% vs base 8%/0.4%/36%. Accuracy at a fixed evidence level is unchanged; the agent commits later. Code declare-lab/RLVB.'
tags:
- rlvr
- agents
- beliefs
- active
---

# RLVB

## Method Overview
RLVB scores commit-vs-continue from the simulator posterior over a hidden answer given the evidence so far. Reward continue while several answers remain possible, and commit once the evidence is sufficient. The update never reads the agent's written belief line, but that line is trained together with the action.

## When to Use
- Long-horizon agents that guess before the evidence is enough, and the environment can compute an exact posterior over a hidden answer.

## When NOT to Use
Programmatic-checker coverage remains `method:canopy`. Pass@1 math/code remains `method:cispo`. Async stragglers remain `method:sao`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:outcome-only-long-horizon-agent-rl`. Distinct from CANOPY, DRACO, Weir, CISPO. Does **not** replace CANOPY or CISPO.

## Gotchas & Failure Modes
- Needs a simulator that knows the evidence-to-answer rules; no judge, critic, or RM substitutes for that posterior.
- GRPO / PPO on outcome reward alone fall below the base model in this setting.
- Gains come from answering with more evidence, not from more accurate answers at the same evidence level.
