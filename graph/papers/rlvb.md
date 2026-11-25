---
id: paper:rlvb
type: paper
title: 'Lazy Agents Answer Against Their Own Beliefs: Reinforcement Learning with Verifiable Beliefs'
authors:
- Richmond Sin
- Jing Xuan
- Peilin Feng
- Wenbin Wang
- Soujanya Poria
year: 2026
month: 11
arxiv_id: '2611.32884'
url: https://arxiv.org/abs/2611.32884
methods:
- method:rlvb
cites: []
tags:
- rlvr
- agents
- beliefs
---

# Lazy Agents Answer Against Their Own Beliefs: Reinforcement Learning with Verifiable Beliefs

## Abstract Summary
Outcome RL trains agents to commit while several answers remain possible. RLVB scores commit-vs-continue from the simulator posterior over a hidden answer and never reads the agent's written belief. The belief line is still trained with the action.

## Key Contributions
1. Simulator-posterior reward for commit vs continue.
2. Belief line is a training target, not a reward input.
3. Pro-Worlds plus two OOD benches on three VLMs.

## Empirical Highlights
+17.1% vs base; +10.4% with EM; +9.3% vs PPO+LLM-judge at 1.6× fewer GPU-h. GRPO and PPO fall below base. Sufficient-evidence answers 51%/12%/74% vs 8%/0.4%/36%. Commit at insufficient evidence 0.1–2.2% vs 3–68%.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.32884`
- Code: `https://github.com/declare-lab/RLVB`
