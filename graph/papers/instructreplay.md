---
id: paper:instructreplay
type: paper
title: 'InstructReplay: Replaying Assistant Turns to Preserve General Behavior During Factual Fine-Tuning'
authors:
- Xiaofeng Shi
- Qian Kou
- Hua Zhou
year: 2026
month: 11
arxiv_id: '2611.32918'
url: https://arxiv.org/abs/2611.32918
methods:
- method:instructreplay
cites: []
tags:
- sft
- replay
- instruct
---

# InstructReplay: Replaying Assistant Turns to Preserve General Behavior During Factual Fine-Tuning

## Abstract Summary
Closed-book factual FT of an instruction-tuned checkpoint collapses generated-answer benches. InstructReplay keeps the student close to frozen M0 answers on a fixed set of general instructions while learning the new facts. The gain is from replaying those assistant turns, not from the loss form.

## Key Contributions
1. Frozen M0 assistant-turn replay mixed with domain NLL.
2. Full next-token match on 9,600 general instructions.
3. Three families × two domains vs seven adaptation methods.

## Empirical Highlights
Standard FT −35 points average; SmolLM3-3B IFEval 71%→9%. InstructReplay general-bench decline 28.1→2.4 while matching standard FT on new facts. BOS-token or domain-answer replay fails.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.32918`
- Code: `https://github.com/xiaofengShi/InstructReplay`
