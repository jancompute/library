---
id: method:modharness-rl
type: method
title: ModHarness-RL
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'building a production engine (rewind, sandbox, remote, TUI)'
    reason: 'omp2 remains the production kernel; ModHarness-RL learns Compression+Steering programs during GRPO'
    use_instead: method:omp2-harness
  - when: 'just-in-time rubric training harness co-evolving with the policy (HarnessRL)'
    reason: 'HarnessRL is a JIT rubric harness; ModHarness-RL is typed State-block Compression+Steering during GRPO'
    use_instead: method:harnessrl
  - when: 'alternating harness+policy optimization (Self-HPO)'
    reason: 'Self-HPO alternates harness and policy; ModHarness-RL proposes/verifies/replays programs inside GRPO'
    use_instead: method:self-hpo
assumptions:
  - 'GRPO agentic RL on CodeSearch / ALFWorld / BIRD with 1.5B–8B policies. Typed State blocks. Project page zlhe0.github.io/ModHarness-RL; no GitHub as of 2026-11-16 (`code_status: none`).'
last_reviewed: '2026-11-16'
papers:
- paper:modharness-rl
recipes:
- recipe:modharness-rl
claims:
- benchmark: 'CodeSearch / ALFWorld / BIRD GRPO, 1.5B–8B vs fixed harness and strongest memory/skill/prompt/harness-evolution baseline'
  metric: 'success vs fixed harness; vs strongest alternative'
  value: 'CodeSearch +14–24% vs fixed harness, +5–12% vs strongest alternative; ALFWorld/BIRD 7/8 settings each program alone wins'
  baseline: 'fixed harness; strongest memory/skill/prompt/harness-evolution baseline'
  date: '2026-11-16'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.18533'
  notes: 'Does not retarget method:omp2-harness. Sibling of method:harnessrl / method:self-hpo / method:activesaddler. Steering is installed only for failures that persist.'
tags:
- harness
- grpo
- agentic-rl
- active
---

# ModHarness-RL

## Method Overview
ModHarness-RL recasts the harness as learnable Compression and Steering programs over typed State blocks. During GRPO it proposes, verifies, and replays those programs. Steering is installed only for failures that persist after Compression.

## When to Use
- Agentic GRPO when a fixed harness is the bottleneck and you can type State into Compression/Steering blocks.

## When NOT to Use
Production kernel remains `method:omp2-harness`. JIT rubric harness remains `method:harnessrl`. Alternating harness+policy remains `method:self-hpo`. Failure-pattern curriculum remains `method:activesaddler`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:agent-harness-runtime`. Does **not** replace omp2.

## Gotchas & Failure Modes
- Learnable programs during GRPO, not a production rewind/sandbox/remote kernel.
- No public GitHub as of 2026-11-16 (`code_status: none`). Project: `https://zlhe0.github.io/ModHarness-RL/`.
