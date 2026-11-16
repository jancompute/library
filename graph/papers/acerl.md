---
id: paper:acerl
type: paper
title: 'Experience-Handoff Reinforcement Learning for Recursive Self-Improvement'
authors:
- Doyoung Kim
- Byeongguk Jeon
- Kailin Zhang
- Sherry Yang
year: 2026
month: 11
arxiv_id: '2611.16409'
url: https://arxiv.org/abs/2611.16409
methods:
- method:acerl
cites: []
tags:
- agent-memory
- grpo
- rsi
- active
---

# Experience-Handoff Reinforcement Learning for Recursive Self-Improvement

## Abstract Summary
ACE-RL freezes the ACE harness and co-optimizes actor, reflector, and curator. Handoff artifacts are rewarded by a downstream actor rollout; per-role GRPO groups keep credit separate. Qwen3-4B-Instruct RSI@3 AppWorld 0.667 vs GRPO-in-harness 0.60; MiniSWEBench 0.340 vs 0.26; Mastermind 0.775 vs 0.74; MBPP 0.987 vs 0.82. No public code. Does not retarget ACE or CANOPY.

## Key Contributions
1. Experience-handoff RL: reward the artifact by the next actor rollout, not a playbook edit score.
2. Per-role GRPO so actor/reflector/curator do not eat each other's credit.
3. Frozen ACE harness; the playbook default stays ACE.

## Empirical Highlights
RSI@3 vs GRPO pass@3: +0.042 / +0.095 / +0.089 / +0.120 on AppWorld / MiniSWEBench / Mastermind / MBPP. RSI@8 0.81 / 0.99 / 0.81 / 0.40 vs GRPO 0.78 / 0.91 / 0.68 / 0.30.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.16409`
- Code: none found (`code_status: none`).
