---
id: paper:booknavigator
type: paper
title: 'Incentivizing Self-Learning in Large Language Models via Reinforcement Learning'
authors:
- Lingkai Kong
- Yuzhe Gu
- Haiteng Zhao
- Zijian Wu
- Youqing Fang
- Zhouqi Hua
- Yanan Sun
- Kai Chen
- Wenwei Zhang
year: 2026
month: 10
arxiv_id: '2610.39671'
url: https://arxiv.org/abs/2610.39671
methods:
- method:booknavigator
cites: []
tags:
- olympiad
- rlvr
- long-context
- active
---

# Incentivizing Self-Learning in Large Language Models via Reinforcement Learning

## Abstract Summary
Textbook-study RL. The model reads a long textbook through BookNavigator (page/section actions) and is scored with fine-grained study rewards before a downstream proof eval. Intern-S2-Preview-35B proof accuracy $51.5\%\to 79.5\%$ vs textbook-free / fixed-context RL. Distinct from Nemotron IMO Gold (TTC / olympiad post-train) and from RLM (dumped-corpus offload). HF Daily 2026-11-12 leftover. No public GitHub as of 2026-11-12.

## Key Contributions
1. BookNavigator: an RL interface over textbook pages and sections rather than a dumped window.
2. Fine-grained study rewards (progress, coverage, retrieval of cited lemmas) instead of a single proof outcome.
3. Gains persist when the textbook is longer than a fixed context.

## Empirical Highlights
Intern-S2-Preview-35B proof accuracy $51.5\%\to 79.5\%$. Does not retarget Nemotron IMO Gold or RLM.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.39671`
- Code: none found (`code_status: none`).
