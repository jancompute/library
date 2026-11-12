---
id: paper:wikitrace
type: paper
title: "Don't Just Trust Your Memory: Evidence-Linked Memory Reduces Memory-Induced Degradation in LLM Agents"
authors:
- Yukyeong Lee
- Yumin Choi
- Jinheon Baek
- Sung Ju Hwang
year: 2026
month: 11
arxiv_id: '2611.14320'
url: https://arxiv.org/abs/2611.14320
methods:
- method:wikitrace
cites: []
tags:
- agent-memory
- active
---

# Don't Just Trust Your Memory: Evidence-Linked Memory Reduces Memory-Induced Degradation in LLM Agents

## Abstract Summary
Write-time lessons inferred from success/failure labels can be wrong; agents that cannot check the source trajectory fail tasks they would solve without memory. WikiTrace stores each insight linked to a compilation and the raw trajectory, then lets the agent descend with terminal tools when an insight is incomplete, conflicting, or from a failed run. Complements `paper:luck-carrying-lessons` and `paper:memory-tax`. Code yukyeongleee/wikitrace released.

## Key Contributions
1. Gain vs Regression split: memory can turn successes into failures; 52% of those failures follow a memory item.
2. Three-layer store: insight → compilation → raw trajectory, with descent at test time.
3. Insights stay frozen after write; the agent reassesses them against source evidence instead of rewriting the playbook.

## Empirical Highlights
Eight suites, five benches. WikiTrace $90.2$ vs No Memory $79.5$ ($+10.7$); vs Insights Only $+3.2$. Regression $6.5\%\to 4.5\%$. Best on every suite. Does not retarget ACE.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.14320`
- Code: `https://github.com/yukyeongleee/wikitrace` (`code_status: released`).
