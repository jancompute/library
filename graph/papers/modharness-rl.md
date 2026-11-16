---
id: paper:modharness-rl
type: paper
title: 'ModHarness-RL: Recasting Harnesses as Learnable and Evolving Programs for Agentic RL'
authors:
- Zelin He
- Siyu Zhu
- Jacob Helwig
- Yujian Liu
- Li An
- Rohit Jain
- Shiyu Chang
- Alborz Geramifard
year: 2026
month: 11
arxiv_id: '2611.18533'
url: https://arxiv.org/abs/2611.18533
methods:
- method:modharness-rl
cites: []
tags:
- harness
- grpo
- agentic-rl
- active
---

# ModHarness-RL: Recasting Harnesses as Learnable and Evolving Programs for Agentic RL

## Abstract Summary
ModHarness-RL learns Compression and Steering programs over typed State blocks during GRPO (propose / verify / replay). Steering is installed only for failures that persist. CodeSearch +14–24% vs a fixed harness, +5–12% vs the strongest memory/skill/prompt/harness-evolution baseline; ALFWorld/BIRD 7/8 settings each program alone wins. 1.5B–8B. No GitHub. Does not retarget omp2.

## Key Contributions
1. Harness as learnable Compression+Steering over typed State, not a frozen prompt.
2. Propose/verify/replay inside GRPO; Steering only for persistent failures.
3. Gains vs fixed harness and vs memory/skill/prompt/harness-evolution baselines.

## Empirical Highlights
CodeSearch +14–24% vs fixed, +5–12% vs strongest alternative. ALFWorld/BIRD 7/8 each program alone wins.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.18533`
- Project: `https://zlhe0.github.io/ModHarness-RL/`
- Code: none found (`code_status: none`).
