---
id: paper:evomemstate
type: paper
title: 'EvoMemState: Evolving Memory State for Personal Agents'
authors:
- Zhishang Xiang
- Yunbo Tang
- Zhongqiao Liu
- Junkai Chen
- Zerui Chen
- Qingguo Hu
- Yuxuan Zhang
- William Grant
- Qinggang Zhang
- Jinsong Su
year: 2026
month: 11
arxiv_id: '2611.03743'
url: https://arxiv.org/abs/2611.03743
methods:
- method:evomemstate
cites:
- paper:ace
- paper:uni-mem
- paper:mdskill
tags:
- agents
- agent-memory
- active
---

# EvoMemState: Evolving Memory State for Personal Agents

## Abstract Summary
EvoMemState keeps persistent facts and adds two evolving states: ontology-guided Relational States (validity, scope, updates, conflicts) and an RL-trained Reasoning State that states applicability, role, and priority for the current request. Distinct from ACE (write-time playbook), Uni-Mem (construction+retrieval GRPO), MDSkill (skill OPSD), and JitMem (read-time trajectory curation).

## Key Contributions
1. Ontology-guided relational memory plus RL reasoning-state policy.
2. MemSyco-Bench Qwen3-8B $57.6\%$ ($+12.2$ vs strongest baseline); GPT-4o-mini $58.9\%$ ($+5.9$).
3. Acc@complete $70.8\%$ LoCoMo-Refined / $68.5\%$ MemSyco ($+11.5$ / $+31.2$).

## Empirical Highlights
HF Daily 2026-11-06 leftover (`2611.03743`). Code XMUDeepLIT/EvoMemState. Does not retarget ACE.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03743`
- Code: `https://github.com/XMUDeepLIT/EvoMemState` (`code_status: released`).
