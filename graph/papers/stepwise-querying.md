---
id: paper:stepwise-querying
type: paper
title: 'Stepwise-Querying: Distilling Reasoning without Access to Teacher Chain-of-Thought'
authors:
- Dicong Yu
- Wenhua Wang
- Tian Wang
year: 2026
month: 10
arxiv_id: '2610.41769'
url: https://arxiv.org/abs/2610.41769
methods:
- method:stepwise-querying
cites:
- paper:traceforge
- paper:opd
tags:
- distillation
- black-box
- active
---

# Stepwise-Querying: Distilling Reasoning without Access to Teacher Chain-of-Thought

## Abstract Summary
Black-box teachers may return only answers and short solutions. Stepwise Querying asks the same teacher independent questions for intermediate derivations, validity checks, and step corrections, then SFT on the assembled solutions. Highest score in 14 of 16 comparisons across two teachers, two students, and four math/code benches. SEIG is a frozen-student log-ratio diagnostic of stepwise vs global explanations.

## Key Contributions
1. Black-box step queries that recover reasoning supervision without teacher CoT traces, then ordinary SFT.

## Empirical Highlights
No public code as of 2026-11-02. Sibling of method:traceforge. Does not retarget method:opd.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.41769`
- Code: none found (`code_status: none`).
