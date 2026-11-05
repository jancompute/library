---
id: paper:harnessflow
type: paper
title: 'HarnessFlow: MCTS-Guided Harness Optimization for LLM Agents'
authors:
- Zhi Hong
- Qianlong Wang
- Hongchen Wei
- Aidan Wu
- Daohong Ying
- Mingze Kong
- Bei Liu
- Chong Luo
year: 2026
month: 11
arxiv_id: '2611.06254'
url: https://arxiv.org/abs/2611.06254
methods:
- method:harnessflow
cites:
- paper:paretosaddler
- paper:harness-playbook
tags:
- agent-harness
- mcts
- rsi
- active
---

# HarnessFlow: MCTS-Guided Harness Optimization for LLM Agents

## Abstract Summary
HarnessFlow organizes full-harness edits in a refinement tree and uses MCTS to spend a limited evaluation budget. A coding agent rewrites complete harness codebases from traces and a component library while the model stays frozen.

## Key Contributions
1. Tree-structured full-harness search with MCTS selection.
2. 15-refinement mean 69.48% across six agent/coding/web benches at 41.4% of Codex cost.

## Empirical Highlights
+10.89 vs vanilla / +3.95 vs Meta-Harness. Does not retarget omp2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.06254`
- Code: none found (`code_status: none`).
