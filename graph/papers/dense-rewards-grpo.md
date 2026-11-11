---
id: paper:dense-rewards-grpo
type: paper
title: 'Are Dense Rewards Worth Their Tokens in GRPO?'
authors:
- Vikash Singh
- Weicong Chen
- Debargha Ganguly
- Yanyan Zhang
- Mohsen Hariri
- Sreehari Sankar
- Wang Yang
- Chaoda Song
- Alexander Nemecek
- Osama Zafar
- Yuting Shao
- Kai Ye
- Biyao Zhang
- Xinpeng Li
- Shouren Wang
- Erman Ayday
- Jing Ma
- Sanmukh Rao Kuppannagari
- Vipin Chaudhary
year: 2026
month: 11
arxiv_id: '2611.13560'
url: https://arxiv.org/abs/2611.13560
methods:
- method:cispo
- method:mcpo
cites:
- paper:minimax-m1
tags:
- rlvr
- process-reward
- grpo
- claim-note
---

# Are Dense Rewards Worth Their Tokens in GRPO?

## Abstract Summary
Claim note, no new method. Matched-compute protocol, $1{,}668$ runs. Monte-Carlo process rewards lead GRPO per update then lose $14.3$ pp at equal tokens and $7.8$ pp at equal GPU-hours on Qwen2.5-1.5B; none of four dense-reward variants beats GRPO at equal time. Continuations are $91\%$ of generated tokens. Prompt selection nearest predicted success $1/2$ gains $+1.7$ / $+0.8$ at matched tokens. Code vicky157/grpo-validation released. Pair with `method:mcpo` (margin credit adds no extra tokens) and `method:tips`. Does not retarget CISPO.

## Key Contributions
1. Matched-compute bake-off: generated tokens and training GPU-hours, not updates.
2. MC process rewards lose $3$–$15$ pp at matched tokens; gradient tests overestimate by $1$–$2$ pp.
3. Prompt filter nearest $1/2$ is the intervention that survives the protocol.

## Empirical Highlights
Qwen2.5-1.5B MC reward $-14.3$ pp vs GRPO at $12.25$ M tokens. Prompt selection $+1.7$ (Qwen3-0.6B) / $+0.8$ (Qwen2.5-1.5B); $2\times$ LR GRPO comes within $0.5$. Complements `paper:credit-helps-hurts` / `paper:what-rl-brings`. Does not retarget CISPO, Cliff, TIPS, or MCPO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.13560`
- Code: `https://github.com/vicky157/grpo-validation` (`code_status: released`).
