---
id: paper:uploop
type: paper
title: 'UpLoop: Training Looped Transformers via Upcycling at No Extra Pretraining Compute'
authors:
- Cheng Liang
- Tengfei Zhang
- Ya Zhang
- Yanfeng Wang
- Zhouhan Lin
year: 2026
month: 10
arxiv_id: '2610.41720'
url: https://arxiv.org/abs/2610.41720
methods:
- method:uploop
cites:
- paper:elr
- paper:smelt
- paper:looped-models-done-right
tags:
- pretraining
- looped-lm
- active
---

# UpLoop: Training Looped Transformers via Upcycling at No Extra Pretraining Compute

## Abstract Summary
UpLoop trains a looped Transformer while matching a dense baseline on final parameter count, total tokens, and training FLOPs. Training starts shallow, copies learned layers to grow depth, and spends the early compute savings on later shared-middle-block loops. At 1.3B the 22-task average rises 22.99 to 27.52; gains also transfer after math SFT.

## Key Contributions
1. FLOP-matched dense looped pretrain via progressive depth copy then shared middle-block loops.

## Empirical Highlights
No public code as of 2026-11-02. Does not retarget method:elr, method:smelt, or method:looped-models-done-right.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.41720`
- Code: none found (`code_status: none`).
