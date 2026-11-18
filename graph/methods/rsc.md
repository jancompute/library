---
id: method:rsc
type: method
title: RSC
category: rl-alignment
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'variable environment latency / async stragglers'
    reason: 'SAO remains the async algorithm; RSC is reverse-KL score centering on off-policy IS, not straggler replay'
    use_instead: method:sao
  - when: 'discrepancy-lag correction of sampler/trainer mismatch (DLC)'
    reason: 'DLC splits numerical discrepancy from policy lag on FP4; RSC is a score-centering trainer, not FP4 alignment'
    use_instead: method:dlc
  - when: 'single-turn dense math/code Pass@1 RLVR'
    reason: 'CISPO remains Pass@1; RSC is reverse-KL score centering of regularized IS'
    use_instead: method:cispo
  - when: 'outcome-only long-horizon agent RL (coverage / anti-drift)'
    reason: 'CANOPY remains coverage; RSC is an off-policy IS stabilizer, not AppWorld group scaling'
    use_instead: method:canopy
assumptions:
  - 'Stale / off-policy token IS where score centering alone still drifts. Paper: Qwen3-4B-Base agentic; sampler refresh R=64. GitHub BiEchi/rsc size 0 as of 2026-11-18. Distinct from paper:score-centering-pg (does not supersede that note).'
last_reviewed: '2026-11-18'
papers:
- paper:rsc
recipes:
- recipe:rsc
claims:
- benchmark: 'AppWorld dev; BabyAI; Crafter; Craftax (Qwen3-4B-Base)'
  metric: 'final evaluation score'
  value: 'AppWorld 14.04 vs SC/SC+TIS 12.28 (+14.3%); BabyAI 18.06 vs IS-PPOClip 1.83 (9.9×); Crafter 14.21 vs 9.34; Craftax 4.71 vs 4.04'
  baseline: 'SC / SC+TIS / IS-PPOClip'
  date: '2026-11-18'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.21791'
  notes: 'Does not retarget method:sao / method:cispo / method:dlc / method:canopy. Does not supersede paper:score-centering-pg. GitHub BiEchi/rsc announced empty.'
tags:
- async-rl
- importance-sampling
- score-centering
- active
---

# RSC

## Method Overview
Regularized Score Centering adds reverse-KL next-token matching to score centering so off-policy IS stays invariant to reward baselines without letting the learner leave the behavior policy. Truncated IS is optional.

## When to Use
- Async / off-policy agent RL where full IS explodes and plain score centering still fails after the learner drifts.

## When NOT to Use
Async stragglers remain `method:sao`. Pass@1 remains `method:cispo`. FP4 train–rollout lag remains `method:dlc`. AppWorld coverage remains `method:canopy`. The theory note remains `paper:score-centering-pg`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:agentic-async-rl`. Mentions on `task:math-code-rl-dense` and `task:outcome-only-long-horizon-agent-rl`. Upgrades `paper:score-centering-pg` into a trainer; does **not** supersede that paper. Does **not** replace SAO, CISPO, DLC, or CANOPY.

## Gotchas & Failure Modes
- GitHub `BiEchi/rsc` is empty as of 2026-11-18 (`code_status: announced`).
- Do not park this on `task:fp4-rl-train-rollout-alignment`; DLC / Fair Cast stay there.
- Do not add `method:rsc` to `paper:score-centering-pg` methods.
