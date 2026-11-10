---
id: paper:aes
type: paper
title: 'Adaptive Entropy-Sparing for Efficient Reasoning'
authors:
- Cong Jiang
- Xiaofeng Zhang
- Tom Ko
- Zheng Zhang
year: 2026
month: 11
arxiv_id: '2611.11901'
url: https://arxiv.org/abs/2611.11901
methods:
- method:aes
cites: []
tags:
- rlvr
- length-control
- entropy
- active
---

# Adaptive Entropy-Sparing

## Abstract Summary
AES is a GRPO-host length controller. It sparsifies high-entropy tokens when a rollout is already correct, and keeps entropy when it is not. R1-1.5B mean acc $64.9\to 68.7$ ($+3.8$), length $6467\to 3048$ ($-52.9\%$); R1-7B $74.1\to 75.2$, $4712\to 2510$. GitHub MobiusDai/AES 404 as of 2026-11-10 (`code_status: announced`). Sibling of LoCo / When2Think / LSD. Does not replace CISPO.

## Key Contributions
1. Entropy-sparing only on already-correct rollouts.
2. Accuracy can rise while length drops, unlike many length penalties.
3. Announced GitHub trainer (404 at ingest).

## Empirical Highlights
R1-1.5B $+3.8$ acc at $-52.9\%$ tokens. R1-7B $+1.1$ acc at roughly half length. Does not retarget CISPO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.11901`
- Code: announced `https://github.com/MobiusDai/AES` (404 as of 2026-11-10).
